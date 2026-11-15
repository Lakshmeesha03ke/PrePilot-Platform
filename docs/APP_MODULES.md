# PrePilot — Application Architecture

**Document:** APP_MODULES.md  
**Version:** 1.0  
**Project:** PrePilot — Career & Recruitment Technology Platform  
**Current Module:** 1.1 — Web Application  
**Status:** Architecture Definition

---

# 1. Web Application Overview

## 1.1 Purpose

The PrePilot Web Application is the primary web platform connecting candidates and employers.

It provides candidates with career preparation, job discovery, application tracking and career development features.

It provides employers with recruitment tools to publish jobs, discover candidates, manage applications and coordinate interviews.

## 1.2 Target Users

1. Candidates — college students, fresh graduates and job seekers.
2. Employers — startups, hiring managers and recruiters.

## 1.3 Technology Stack

| Technology | Purpose |
|---|---|
| Next.js | Web application framework |
| TypeScript | Type-safe development |
| Tailwind CSS | UI styling |
| React | Component-based interface |
| REST API | Backend communication |
| PostgreSQL | Application data through backend |
| Prisma | Database access through backend |

**Architecture rule:** The web application must never connect directly to the production database. All business operations must go through the backend API.

---

# 2. Application Structure

The Web Application contains two primary user experiences.

### A. Candidate Portal

Designed for students and fresh graduates.

### B. Employer Portal

Designed for companies and recruiters.

Both portals will use the same web application but have separate access permissions, dashboards and workflows.

---

# 3. Candidate Portal — Features

## 3.1 Authentication & Account Management

- Candidate registration
- Login and logout
- Email verification
- Password reset
- Secure session management
- Account settings

## 3.2 Candidate Profile Management

- Personal information
- Educational qualifications
- College and university details
- Technical skills
- Projects
- Internships
- Certifications
- Work experience
- Career interests

## 3.3 Resume Management

- Upload resume
- View resume
- Replace resume
- Delete resume
- Resume version management
- Resume completeness indicator

## 3.4 Candidate Dashboard

Display:

- Profile completion
- Placement readiness score
- Recommended activities
- Recent job opportunities
- Application status
- Upcoming interviews
- Notifications
- Career progress

## 3.5 Job Discovery

- Browse available jobs
- Search jobs
- Filter by skills
- Filter by location
- Filter by job type
- View job descriptions
- View eligibility requirements
- Save jobs

## 3.6 Job Application Management

- Apply for jobs
- Submit required information
- Track applications
- Withdraw applications where permitted
- View application status
- Receive recruitment updates

## 3.7 Skill Assessment

Assess candidate readiness across:

1. Aptitude
2. Coding and DSA
3. Core computer science
4. Technical interviews
5. HR interviews
6. Resume readiness

## 3.8 AI Career Assistant

- Explain technical concepts
- Support interview preparation
- Provide career guidance
- Generate practice questions
- Recommend learning activities

## 3.9 Notifications

- Application updates
- Interview invitations
- Job recommendations
- Assessment reminders
- Important account notifications

---

# 4. Employer Portal — Features

## 4.1 Employer Authentication

- Employer registration
- Login and logout
- Email verification
- Password reset
- Secure sessions
- Employer account settings

## 4.2 Company Profile

- Company name
- Company description
- Website
- Industry
- Company logo
- Location
- Company verification status

## 4.3 Employer Dashboard

Display:

- Active job postings
- Total applications
- New applicants
- Shortlisted candidates
- Interviews scheduled
- Recruitment activity

## 4.4 Job Management

- Create job postings
- Edit job postings
- Publish jobs
- Pause applications
- Close job postings
- Define eligibility criteria
- Specify required skills
- Define salary information

## 4.5 Applicant Management

- View applicants
- Review candidate profiles
- View submitted resumes
- Shortlist candidates
- Reject applications
- Change application status
- Add internal recruitment notes

## 4.6 Candidate Discovery

- Search candidates
- Filter by skills
- Filter by education
- Filter by experience
- Review candidate profiles

## 4.7 Interview Management

- Schedule interviews
- Share interview details
- Manage interview status
- Update interview outcomes

## 4.8 Recruitment Analytics

- Job application statistics
- Candidate pipeline
- Shortlisting statistics
- Hiring progress
- Recruitment activity reports

---

# 5. Web Application Route Structure

Proposed route organisation:

## Public Routes

- `/`
- `/about`
- `/jobs`
- `/jobs/[jobId]`
- `/login`
- `/register`

## Candidate Routes

- `/candidate/dashboard`
- `/candidate/profile`
- `/candidate/resume`
- `/candidate/jobs`
- `/candidate/applications`
- `/candidate/assessments`
- `/candidate/assistant`
- `/candidate/notifications`
- `/candidate/settings`

## Employer Routes

- `/employer/dashboard`
- `/employer/company`
- `/employer/jobs`
- `/employer/jobs/create`
- `/employer/applicants`
- `/employer/candidates`
- `/employer/interviews`
- `/employer/analytics`
- `/employer/settings`

These are proposed routes. Their final implementation will follow the approved access-control and navigation design.

---

# 6. UI/UX Requirements

- Premium professional appearance
- Responsive desktop, tablet and mobile layouts
- Light theme
- Dark theme
- Consistent navigation
- Reusable UI components
- Accessible forms and controls
- Clear loading and error states
- Consistent typography and spacing

---

# 7. Security Requirements

- Role-based access control
- Secure authentication
- Protected candidate and employer routes
- Server-side authorization
- Input validation
- Safe file upload handling
- Rate limiting for sensitive operations
- Secure session and token handling
- Protection against common web vulnerabilities

A user interface permission check is not sufficient. The backend must independently verify authorization for every protected operation.

---

# 8. Web Application and Backend Communication

The Web Application communicates with the PrePilot API through versioned REST endpoints.

Proposed API base path:

`/api/v1`

Examples:

- Candidate authentication
- Candidate profile management
- Resume operations
- Job discovery
- Job applications
- Employer job management
- Applicant management
- Interview management

The API is responsible for business rules, authorization, database operations and validation.

---

# 9. Development Phases

### Phase 1 — Foundation

- Next.js project setup
- TypeScript configuration
- Tailwind CSS setup
- Application layout
- Routing
- Theme foundation

### Phase 2 — Authentication

- Candidate registration and login
- Employer registration and login
- Session handling
- Protected routes

### Phase 3 — Candidate Portal

- Candidate profile
- Resume management
- Candidate dashboard
- Job discovery
- Applications

### Phase 4 — Employer Portal

- Company profile
- Employer dashboard
- Job management
- Applicant management
- Interviews

### Phase 5 — Advanced Features

- Skill assessments
- AI assistant
- Notifications
- Analytics

### Phase 6 — Quality Assurance

- Functional testing
- Security testing
- Responsive testing
- Performance testing
- Accessibility testing

---

# 10. Definition of Completion

The Web Application module will be considered complete only when:

- Candidate and employer experiences are implemented.
- Authentication and authorization work correctly.
- Core candidate workflows work.
- Core employer workflows work.
- Backend integration works.
- Responsive layouts are tested.
- Security checks are completed.
- Major functional defects are resolved.

**Important:** This document defines the intended Web Application scope. Features will be implemented incrementally, not all at once.



---

# Module 1.2 — Mobile Application

**Status:** Architecture Definition  
**Platforms:** Android and iOS

## 1. Purpose

The PrePilot Mobile Application provides candidates and employers with access to recruitment and career services through Android and iOS devices.

## 2. Technology Stack

- React Native
- Expo
- TypeScript
- Expo Router
- REST API integration
- Secure local storage
- Push notification integration

## 3. Application Modules

### 3.1 Authentication
- Candidate registration
- Employer registration
- Login and logout
- Password recovery
- Session management

### 3.2 Candidate Profile
- Personal information
- Education details
- Skills
- Projects
- Internships
- Certifications

### 3.3 Resume Management
- Upload resume
- View resume
- Replace resume
- Manage resume versions

### 3.4 Candidate Dashboard
- Placement readiness score
- Profile completion
- Recommended tasks
- Career progress
- Recent activities

### 3.5 Job Discovery
- Browse jobs
- Search jobs
- Filter opportunities
- View job descriptions
- Save jobs

### 3.6 Job Applications
- Apply for jobs
- Track applications
- View application status
- Receive updates

### 3.7 Skill Assessment
- Aptitude assessment
- Coding and DSA assessment
- Core CS assessment
- Technical interview preparation
- HR interview preparation
- Resume readiness

### 3.8 AI Assistant
- Technical explanations
- Interview preparation
- Practice questions
- Career recommendations

### 3.9 Employer Features
- Employer dashboard
- Company profile management
- Job posting management
- Applicant review
- Candidate shortlisting
- Interview management

### 3.10 Notifications
- Application updates
- Interview reminders
- Job recommendations
- Important announcements

## 4. Navigation Structure

### Candidate Navigation
- Home
- Explore Jobs
- Applications
- Preparation
- Profile

### Employer Navigation
- Dashboard
- Jobs
- Applicants
- Interviews
- Company Profile

## 5. Mobile Requirements

- Android and iOS compatibility
- Responsive layouts for different screen sizes
- Light and dark themes
- Secure authentication
- Smooth navigation
- Appropriate loading and error states
- Accessible interface
- Push notification support

## 6. Backend Integration

The mobile application communicates with the same PrePilot REST API used by the web application.

Proposed API prefix: `/api/v1`

The mobile application must not directly access the production database.

## 7. Security Requirements

- Secure session storage
- Backend authorization
- Role-based access
- Secure API communication
- Safe document upload
- Input validation
- Protection of sensitive user information

## 8. Development Phases

1. Expo project setup
2. Navigation and application foundation
3. Authentication
4. Candidate application
5. Employer application
6. Backend integration
7. Notifications and AI integration
8. Testing and optimization

## 9. Definition of Completion

- Android and iOS builds work.
- Candidate workflows work.
- Employer workflows work.
- API integration works.
- Authentication is secure.
- Notifications work as intended.
- Device compatibility is tested.
- Major functional defects are resolved.

**Architecture rule:** Mobile and Web share backend services and business rules, but maintain platform-appropriate user interfaces.





---

# Module 1.3 — Backend API

**Status:** Architecture Definition  
**Framework:** NestJS  
**Language:** TypeScript  
**API Style:** REST  
**API Version:** v1

## 1. Purpose

The PrePilot Backend API acts as the central communication and business logic layer of the platform.

It connects the Web Application, Mobile Application, Admin Application, database and supporting services.

## 2. Technology Stack

- NestJS
- TypeScript
- PostgreSQL
- Prisma ORM
- Redis
- BullMQ
- REST API
- Swagger / OpenAPI

## 3. Core API Modules

### 3.1 Authentication Module
- Candidate registration
- Employer registration
- Login and logout
- Email verification
- Password reset
- Session management
- Authentication authorization

### 3.2 User Module
- User account management
- User information
- Account status
- User preferences

### 3.3 Candidate Module
- Candidate profile management
- Education details
- Skills
- Projects
- Internships
- Certifications

### 3.4 Employer Module
- Employer account management
- Company profile
- Company verification
- Recruiter information

### 3.5 Resume Module
- Resume upload
- Resume retrieval
- Resume deletion
- Resume version management
- File validation

### 3.6 Job Module
- Create jobs
- Update jobs
- Publish jobs
- Close jobs
- Search jobs
- Filter jobs
- Retrieve job details

### 3.7 Application Module
- Submit applications
- Retrieve applications
- Track application status
- Shortlist candidates
- Reject applications
- Update recruitment status

### 3.8 Assessment Module
- Aptitude assessments
- Coding assessments
- DSA assessments
- Core CS assessments
- Technical interview assessments
- HR interview assessments
- Assessment results

### 3.9 AI Module
- AI assistant integration
- Career recommendations
- Interview preparation
- Question generation
- AI provider integration

### 3.10 Interview Module
- Schedule interviews
- Update interview details
- Track interview status
- Store interview outcomes

### 3.11 Notification Module
- In-app notifications
- Email notifications
- Push notification integration
- Notification preferences

### 3.12 Analytics Module
- Candidate statistics
- Employer statistics
- Job application statistics
- Recruitment reports

### 3.13 Admin Module
- User management
- Employer management
- Job moderation
- Platform monitoring
- Administrative actions
- Audit logs

## 4. API Structure

Base API path:

`/api/v1`

Proposed endpoints:

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/auth/register` | Register account |
| POST | `/auth/login` | Authenticate user |
| GET | `/candidates/me` | Get candidate profile |
| PUT | `/candidates/me` | Update candidate profile |
| GET | `/jobs` | Discover jobs |
| GET | `/jobs/:id` | Retrieve job details |
| POST | `/jobs` | Create job |
| POST | `/applications` | Submit application |
| GET | `/applications/me` | Retrieve own applications |
| GET | `/employers/me` | Retrieve employer profile |

These are initial endpoint examples, not the complete API specification.

## 5. Authentication and Authorization

- Secure authentication
- Role-based access control
- Candidate permissions
- Employer permissions
- Administrator permissions
- Protected API endpoints
- Session and token security

All authorization decisions must be enforced on the backend.

## 6. Database Communication

The API communicates with PostgreSQL through Prisma ORM.

Responsibilities include:

- Data creation
- Data retrieval
- Data updates
- Data deletion
- Database transactions
- Data integrity
- Relationship management

Applications must not access the database directly.

## 7. Validation and Error Handling

- Request validation
- Response consistency
- Centralized exception handling
- Meaningful error messages
- HTTP status codes
- Request size limits
- Rate limiting

## 8. API Documentation

Swagger / OpenAPI will document:

- Available endpoints
- Request parameters
- Request body schemas
- Response schemas
- Authentication requirements
- Error responses

## 9. Security Requirements

- HTTPS in deployed environments
- Password hashing
- Input validation
- SQL injection protection
- Authorization checks
- Rate limiting
- Secure file handling
- Audit logging
- Sensitive data protection
- Secret management

## 10. Development Phases

1. NestJS project initialization
2. Configuration and environment setup
3. Database connection
4. Authentication module
5. User and profile modules
6. Job and application modules
7. Employer and recruitment modules
8. Assessment and AI modules
9. Notifications and analytics
10. Security testing and API testing

## 11. Definition of Completion

- API modules are implemented.
- Authentication works correctly.
- Authorization is enforced.
- Database integration works.
- Web and Mobile can communicate with the API.
- Input validation and error handling work.
- Swagger documentation is available.
- Security and functional tests pass.

**Architecture rule:** The Backend API is the authoritative source for business logic, permissions and data operations across PrePilot.




---

# Module 1.4 — Admin Application

**Status:** Architecture Definition  
**Purpose:** Platform Administration and Management

## 1. Overview

The PrePilot Admin Application is a restricted administrative interface for managing platform operations, users, employers, job postings, content, support requests and system activities.

It is accessible only to authorized administrators.

## 2. Admin Roles

### 2.1 Super Admin
- Complete platform administration
- Manage administrator accounts
- Assign administrative permissions
- Manage global platform settings
- Access platform-wide reports
- Review audit logs

### 2.2 Platform Admin
- Manage candidate accounts
- Manage employer accounts
- Review company verification requests
- Moderate job postings
- Monitor platform activity

### 2.3 Support Admin
- View support requests
- Handle reported issues
- Assist users
- Track complaint resolution

Each role must have explicitly defined permissions. Administrative access must follow least-privilege principles.

## 3. Core Admin Modules

### 3.1 Admin Authentication
- Secure admin login
- Session management
- Password recovery
- Multi-factor authentication support
- Role-based access control

### 3.2 Admin Dashboard
- Total candidates
- Total employers
- Active job postings
- Total applications
- Pending verification requests
- Reported content
- Platform activity

### 3.3 User Management
- View candidate accounts
- Search users
- Filter users
- View account details
- Suspend accounts when justified
- Restore accounts
- Manage reported users

### 3.4 Employer Management
- View employer accounts
- Review company information
- Review verification requests
- Approve or reject verification
- Suspend employer accounts when justified

### 3.5 Job Moderation
- Review job postings
- Identify suspicious job postings
- Approve or reject flagged content
- Remove policy-violating postings
- Review reported jobs

### 3.6 Application Monitoring
- Monitor application statistics
- Track recruitment activity
- Investigate reported issues
- View application pipeline metrics

### 3.7 Content Management
- Manage announcements
- Manage platform information pages
- Manage help content
- Manage platform guidelines

### 3.8 Reports and Analytics
- Candidate statistics
- Employer statistics
- Job statistics
- Application statistics
- Platform usage reports

### 3.9 Support Management
- View user support requests
- Assign support tickets
- Update ticket status
- Track issue resolution
- Maintain support history

### 3.10 Audit Logs
- Record administrative actions
- Record account status changes
- Track moderation decisions
- Record permission changes
- Maintain administrative activity history

### 3.11 System Settings
- Platform configuration
- Feature availability
- Notification configuration
- Maintenance settings

## 4. Admin Navigation

Proposed navigation:

- Dashboard
- Candidates
- Employers
- Job Moderation
- Applications
- Content Management
- Reports
- Support
- Audit Logs
- Settings

## 5. Security Requirements

- Separate administrator authentication
- Role-based access control
- Multi-factor authentication support
- Strong session management
- Least-privilege permissions
- Server-side authorization
- Audit logging
- Sensitive data protection
- Rate limiting
- Secure administrative operations

All sensitive administrative actions must be authorized and recorded.

## 6. Backend Integration

The Admin Application communicates with the Backend API using protected administrative endpoints under `/api/v1`.

The backend independently verifies the administrator's identity, role and permissions.

## 7. Development Phases

1. Admin application foundation
2. Admin authentication
3. Role and permission management
4. Admin dashboard
5. User management
6. Employer management
7. Job moderation
8. Reports and analytics
9. Support management
10. Audit logs and security testing

## 8. Definition of Completion

- Authorized administrators can log in.
- Permissions are correctly enforced.
- User and employer management works.
- Job moderation works.
- Administrative actions are audited.
- Reports display accurate data.
- Security and functional tests pass.

**Architecture rule:** The Admin Application is a restricted platform-management interface. It must never rely on frontend-only permission checks for administrative security.





# Architecture Decision Update — PrePilot

## 1. Confirmed Technology Stack

- Web Application: Next.js + TypeScript
- Mobile Application: React Native + Expo
- Backend API: NestJS + TypeScript
- Database: PostgreSQL
- ORM: Prisma
- Background Processing: Redis + BullMQ (introduced when required)
- File Storage: S3-compatible object storage
- API Architecture: REST API with versioning
- AI Integration: Provider-independent AI integration layer
- Code Execution: Isolated code execution solution

## 2. Application Architecture Decisions

### Web Application
The main web application will support candidates and employers.

### Mobile Application
The mobile application will initially focus on candidate placement preparation and career development.

### Backend API
A modular monolith architecture will be used. All major business features will be organised into independent backend modules.

### Admin Application
Initially, the admin dashboard will be integrated into the main Next.js web application with separate authentication and role-based access control.

A separate admin application may be considered in the future if necessary.

## 3. Development Strategy

- Build the placement preparation MVP first.
- Develop the backend and database foundation before connecting all applications.
- Introduce additional services only when required.
- Prioritise security, maintainability and performance.
- Expand into job discovery and employer recruitment in later phases.

## 4. Architecture Status

These are the approved initial architecture decisions for PrePilot. Technologies and infrastructure may be revised when actual requirements justify a change.




## Backend Architecture Decision

### Architecture Pattern
Modular Monolith.

### Backend Technology
NestJS + TypeScript.

### Database
PostgreSQL with Prisma ORM.

### API Style
REST API with versioning: `/api/v1`.

### Backend Organisation
The backend will contain independent modules for:
- Authentication
- Users and Candidates
- Assessments
- Aptitude
- DSA
- Core CS
- AI Assistant
- Resume Management
- Jobs and Applications
- Employers
- Notifications
- Administration

### Development Principle
Start with one backend application. Introduce separate services only when technical requirements justify them.

This architecture prioritises simplicity, maintainability, security and future scalability.