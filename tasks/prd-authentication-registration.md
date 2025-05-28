Here's the complete PRD:

# Authentication and Registration System PRD

## Introduction/Overview
This document outlines the requirements for implementing a comprehensive authentication and registration system for the web application. The system will handle user authentication, first-time user registration, and school/campus information collection. The goal is to provide secure access while ensuring proper data collection for educational institutions.

## Goals
- Implement a secure authentication system with multiple login methods
- Provide a streamlined first-time user registration process
- Collect necessary school and campus information
- Ensure data security and user account protection
- Support multiple authentication recovery methods

## User Stories
1. As a new user, I want to create an account so that I can access the system
2. As a registered user, I want to log in using my email and password so that I can access my account
3. As a user who forgot their password, I want to request a magic link or reset password so that I can regain access
4. As a school administrator, I want to provide my school and campus information during registration so that I can set up my organization
5. As a locked-out user, I want to verify my identity through alternative methods so that I can regain access

## Functional Requirements

### 1. Authentication System
1.1. Login Methods
- System must support email/password authentication
- System must support magic link authentication
- System must implement JWT token-based session management

1.2. Password Requirements
- Minimum 8 characters
- Must contain at least 1 capital letter
- Must contain at least 1 special character
- System must validate password requirements during registration and password reset

1.3. Session Management
- Sessions must remain active for 10 hours
- System must automatically log out users after session expiration
- System must allow users to manually log out

1.4. Security Measures
- Implement rate limiting for login attempts
- Lock account temporarily after 7 unsuccessful login attempts
- Provide generic error messages to prevent user enumeration
- Implement secure password hashing and storage

1.5. Account Recovery
- Support password reset via email link
- Support magic link authentication (valid for 10 minutes)
- Support phone number verification as backup recovery method
- Send generic success messages for recovery attempts

### 2. Registration System
2.1. User Information
- Collect first name (required)
- Collect last name (required)
- Collect email address (required)
- Collect phone number (required)
- Collect and validate password (required)
- Verify password confirmation matches

2.2. Email Verification
- Send verification email after registration
- Allow access to basic features before verification
- Require email verification before accessing schedule creation features in page area E
- Provide option to resend verification email

### 3. School/Campus Information
3.1. Required Fields
- School name
- Campus name
- Street address
- City
- State (dropdown selection)
- Postal code
- Email address
- Phone number

3.2. Optional Fields
- Facility license
- Tax ID
- School motto
- Logo upload (max 2MB)

### 4. Logo Management
4.1. Upload Requirements
- Maximum file size: 2MB
- Server-side image processing for cropping and resizing
- No client-side image editing required

## Non-Goals (Out of Scope)
- Social media authentication integration
- Multi-factor authentication
- Custom password requirements per organization
- Client-side image editing
- Real-time facility license or tax ID validation
- Multiple campus creation during initial registration

## Technical Considerations
- Implement secure password hashing (e.g., bcrypt)
- Use JWT for session management
- Implement rate limiting middleware
- Set up secure email delivery system
- Configure server-side image processing
- Store sensitive data in encrypted format
- Implement proper CORS and CSP headers

## Success Metrics
- Successful user registration completion rate > 90%
- Password reset success rate > 95%
- Account recovery completion rate > 90%
- System uptime > 99.9%
- Average login time < 2 seconds

## Open Questions
1. Should we implement a grace period for email verification?
2. Should we allow users to change their email address after registration? 
3. What should be the cool-down period after an account is temporarily locked?
4. Should we implement progressive rate limiting before complete account lockout?

## Notes
- Additional campuses can be created for the organization through the settings page after initial organization registration
- The system should be designed to scale for multi-campus organizations
- All error messages should be user-friendly while maintaining security
- Consider implementing logging for security-related events

