# Angular 21 Auth Boilerplate

A full-featured Angular 21 authentication boilerplate with sign up, email verification, login, JWT refresh tokens, and role-based access control.

## Features

- ✅ Email sign up & verification
- ✅ JWT authentication with refresh tokens (auto-renew 1 min before expiry)
- ✅ Role-based authorization (User & Admin roles)
- ✅ Forgot password & reset password
- ✅ View & update profile
- ✅ Admin section — manage all accounts (Admin only)
- ✅ Fake backend API (runs entirely in browser, no server needed)
- ✅ Styled with Bootstrap 5

## Getting Started

### Prerequisites
- Node.js 20+
- Angular CLI 21

### Install Angular CLI
```bash
npm install -g @angular/cli@21
```

### Install dependencies
```bash
npm install
```

### Run the app
```bash
ng serve
```

Open [http://localhost:4200](http://localhost:4200)

## How It Works

### Fake Backend
The app runs with a fake backend by default. It intercepts HTTP requests and simulates a real API using `localStorage`.

After registering, a fake "verification email" appears on screen — click the link to verify and log in.

### First Account = Admin
The first account registered gets the **Admin** role. All subsequent accounts get the **User** role.

### JWT Flow
- JWT access token expires in **15 minutes**
- Refresh token expires in **7 days**
- The app auto-refreshes the JWT **1 minute before expiry**

## Project Structure

```
src/app/
├── _components/     # Shared components (AlertComponent)
├── _helpers/        # Guards, interceptors, validators, fake backend
├── _models/         # TypeScript interfaces/models
├── _services/       # Account & Alert services
├── account/         # Login, Register, Verify Email, Forgot/Reset Password
├── admin/           # Admin section with accounts management
├── home/            # Home page (protected)
└── profile/         # View & update profile (protected)
```

## Connecting a Real API

To use a real backend, remove `fakeBackendProvider` from `app.module.ts` and set `apiUrl` in `src/environments/environment.ts`.

Compatible backends:
- [.NET API](https://jasonwatmore.com/post/2022/02/26/net-6-boilerplate-api-tutorial-with-email-sign-up-verification-authentication-forgot-password)
- [Node.js + MongoDB API](https://jasonwatmore.com/post/2022/02/26/nodejs-mongodb-boilerplate-api-tutorial)
- [Node.js + MySQL API](https://jasonwatmore.com/post/2022/02/26/nodejs-mysql-boilerplate-api-tutorial)
