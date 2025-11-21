It looks like you'll need to log in to ChatGPT to use the Canvas feature for generating a file. However, I can still provide the dev outline in markdown here, and you can copy it directly into your project files.

Here’s a concrete development outline for your "forgot password" and "admin account creation" features in NestJS, Prisma, and Supabase with JWT:

---

## Feature Outline: Password Reset & Admin Account Creation

### **1. Overview**

This feature will implement:

* **Password Reset** via an OTP sent to the user’s email address.
* **Admin Account Creation** via the admin dashboard with email verification.

Technologies:

* Backend: NestJS, Prisma
* Authentication: JWT
* Database: Supabase (Postgres)
* Frontend: React

---

### **2. Password Reset Flow**

#### 2.1. **Password Reset Request (Frontend)**

* **Route**: `/forgot-password`
* **Fields**:

  * Email (user submits their email to receive the OTP).

##### Frontend (React):

* User submits email.
* Call `POST /auth/forgot-password` with the email.
* Show success or error message based on response.

---

#### 2.2. **Password Reset Request (Backend)**

* **Route**: `POST /auth/forgot-password`
* **Functionality**:

  * Accept email from the user.
  * Validate if email exists in the system.
  * Generate an OTP token (JWT) with a short expiry (e.g., 10-15 minutes).
  * Send OTP to user’s email with a reset link.

    * Include the JWT token as a URL parameter (e.g., `/reset-password?token=<jwt_token>`).

##### NestJS Implementation:

* **Service**: `AuthService`

  * Method: `forgotPassword(email: string)`

    * Check if user exists.
    * Generate OTP JWT.
    * Use an email service (Supabase’s email service or external provider like SendGrid) to send the OTP email.

```ts
async forgotPassword(email: string) {
  const user = await this.prisma.user.findUnique({ where: { email } });
  if (!user) throw new NotFoundException('User not found');
  
  const token = this.jwtService.sign({ email: user.email }, { expiresIn: '15m' });
  
  await this.emailService.sendPasswordResetEmail(user.email, token);
}
```

---

#### 2.3. **Password Reset (Frontend)**

* **Route**: `/reset-password?token=<jwt_token>`
* **Fields**:

  * New Password
  * Confirm New Password

##### Frontend (React):

* Display form to enter the new password.
* Submit password reset request to backend with new password and JWT token.

---

#### 2.4. **Password Reset (Backend)**

* **Route**: `POST /auth/reset-password`
* **Functionality**:

  * Validate JWT token in the query string.
  * Check if the token is valid and not expired.
  * Reset the password to the new one.
  * Invalidate the JWT token (one-time use).

##### NestJS Implementation:

* **Service**: `AuthService`

  * Method: `resetPassword(token: string, newPassword: string)`

    * Verify the JWT token.
    * Hash the new password (using bcrypt).
    * Update the user’s password in the database.

```ts
async resetPassword(token: string, newPassword: string) {
  const payload = this.jwtService.verify(token);
  const user = await this.prisma.user.findUnique({ where: { email: payload.email } });
  if (!user) throw new NotFoundException('User not found');
  
  const hashedPassword = await bcrypt.hash(newPassword, 10);
  await this.prisma.user.update({ where: { email: payload.email }, data: { password: hashedPassword } });
}
```

---

### **3. Admin Account Creation**

#### 3.1. **Admin Interface (Frontend)**

* **Route**: `/admin/create-account`
* **Fields**:

  * Name
  * Email
  * Role (admin, user, etc.)
  * Password

##### Frontend (React):

* Admin can create a new account by filling out the form.
* Submit a `POST /admin/create-account` request with the form data.

---

#### 3.2. **Admin Account Creation (Backend)**

* **Route**: `POST /admin/create-account`
* **Functionality**:

  * Validate admin’s authentication (ensure the requester is an admin).
  * Create a new user in the database with the provided details.
  * Optionally, send an email verification link (via JWT token) to confirm account creation.
  * Admin can set roles (admin or user).

##### NestJS Implementation:

* **Service**: `AdminService`

  * Method: `createAccount(createAccountDto: CreateAccountDto)`

    * Ensure the requester is an admin.
    * Create the new user in the database with Prisma.
    * Optionally, send a verification email for account activation.

```ts
async createAccount(createAccountDto: CreateAccountDto) {
  const { email, name, role, password } = createAccountDto;
  
  // Check if the admin already exists
  const existingUser = await this.prisma.user.findUnique({ where: { email } });
  if (existingUser) throw new BadRequestException('User already exists');
  
  // Create new user
  const hashedPassword = await bcrypt.hash(password, 10);
  const newUser = await this.prisma.user.create({
    data: { email, name, role, password: hashedPassword },
  });

  // Optionally, send email for activation
  const token = this.jwtService.sign({ email: newUser.email }, { expiresIn: '24h' });
  await this.emailService.sendActivationEmail(newUser.email, token);
}
```

---

#### 3.3. **Email Verification for Admin Creation**

* After account creation, an email with an activation link (containing a JWT token) is sent to the user.
* The user clicks the link and is redirected to a frontend page where their account is activated.

##### Frontend (React):

* The link leads to `/activate-account?token=<jwt_token>`.
* When the user accesses the page, the frontend sends a `POST /auth/activate-account` request with the JWT token.

#### 3.4. **Account Activation (Backend)**

* **Route**: `POST /auth/activate-account`
* **Functionality**:

  * Verify the JWT token and activate the account.
  * Set the account’s `isActive` flag to `true`.

##### NestJS Implementation:

```ts
async activateAccount(token: string) {
  const payload = this.jwtService.verify(token);
  const user = await this.prisma.user.findUnique({ where: { email: payload.email } });
  
  if (!user) throw new NotFoundException('User not found');
  
  await this.prisma.user.update({ where: { email: user.email }, data: { isActive: true } });
}
```

---

### **4. Testing & Security Considerations**

* **Test Cases**:

  * Password reset (valid/invalid token).
  * Admin creation and email verification.
  * Handle edge cases like expired tokens, non-existent users, and password mismatches.

* **Security**:

  * Ensure password hashing (bcrypt) is used for storage.
  * Use JWT expiration times to limit the validity of reset tokens and activation links.
  * Use secure email sending and prevent spam folder issues.

---

This outline should give you a solid base to start implementing the features in NestJS, Prisma, and Supabase. Let me know if you need more detailed explanations or adjustments!

