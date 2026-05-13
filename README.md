#NextJS Authentication Backend System

A scalable and secure backend authentication system built using NestJS, TypeScript, and MongoDB. This project demonstrates production-oriented backend engineering practices including JWT authentication, refresh token management, password encryption, email-based password recovery, modular architecture, and REST API development

The system is designed as the backend foundation for modern web and mobile applications such as e-commerce platforms, SaaS products, admin dashboards, and user management systems. It follows a clean modular architecture and emphasizes security, scalability, maintainability, and real-world authentication workflows

Project setup
$ npm install

Compile and run the project
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod

Run tests
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov

Tech Stack
NestJS — backend framework
TypeScript — strongly typed language
MongoDB — database
Mongoose — schema/model handling
JWT — authentication
Passport — auth strategies
bcrypt — password encryption
Nodemailer — email service

Main Features
1. User Signup
   The project allows users to create accounts.

Flow:
User sends:
username
email
password
Backend validates:
empty fields
email format
password length
Password gets hashed using bcrypt.
User data stored in MongoDB.
JWT access token + refresh token generated

Important Security Part
Password is never stored directly.
Example
const hashedPassword = await bcrypt.hash(password, 10); #typescript

2.Login System
The login flow:
User enters email + password
System checks if user exists
bcrypt compares password hashes
JWT token returned
Example response
{
  "accessToken": "...",
  "refreshToken": "..."
}

3. JWT Authentication
   This project uses JWT authentication
   Access Token
   Short-lived token:
   signOptions: { expiresIn: '1h' }#typescript
   Used for:

protected routes
user authorization

4. Refresh Token System
This is one of the better parts of the project.
Instead of forcing the user to login repeatedly:
Access token expires in 1 hour
Refresh token generates a new access token
Refresh tokens are:
stored in MongoDB
given expiration dates
rotated after use
This is close to production-level auth architecture

5. Password Reset System
The project includes:
Change Password
Requires:
old password
new password
Checks:
old password correctness
password length
prevents same password reuse

Architecture Style

This project follows modular architecture from NestJS.
Modules:
AuthModule
UsersModule
EmailModule
Benefits:
scalable
maintainable
enterprise-style organization
   
