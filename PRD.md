# Product Requirements Document (PRD) — MVP

## Vision

Build the leading recruitment platform for Africa that connects job seekers, employers, recruiters, and educational institutions through a modern hiring ecosystem. The platform should reduce hiring time, improve candidate quality, and provide a trusted, fraud-resistant experience.

## Mission

Help people find meaningful work while enabling organizations to hire the right talent faster and more efficiently.

## Problem Statement

Current job platforms suffer from several issues:

- Fake job postings
- Fake recruiter profiles
- Poor candidate-job matching
- Slow hiring processes
- Limited recruiter collaboration tools
- Poor applicant tracking
- Outdated user experiences
- Lack of transparency for both employers and job seekers

Our platform aims to solve these problems with modern workflows, automation, and intelligent matching.

## Target Market

### Phase 1
- Nigeria

### Phase 2
- Ghana
- Kenya
- South Africa
- Egypt

### Phase 3
- Rest of Africa

### Phase 4
- Global hiring and remote recruitment

## Target Users

### Job Seekers
- Students
- Graduates
- Professionals
- Freelancers
- Remote workers
- Skilled trades
- Blue-collar workers

### Employers
- Startups
- SMEs
- Enterprises
- Government agencies
- NGOs

### Recruiters
- Internal recruiters
- Recruitment agencies
- Independent recruiters

### Platform Administrators
- Support
- Moderation
- Finance
- Compliance
- Operations

## Core Value Proposition

Instead of just posting jobs, the platform manages the complete hiring lifecycle:

```
Find Talent
      ↓
    Apply
      ↓
   Screen
      ↓
Interview
      ↓
   Offer
      ↓
    Hire
      ↓
Onboard (Future)
```

## MVP Scope (Version 1)

Focus on delivering a fast, reliable recruitment experience with the essentials.

### Authentication

#### Job Seeker
- Email/password login
- Google OAuth
- Email verification
- Forgot password
- JWT authentication
- Refresh tokens
- Two-factor authentication (optional)

#### Employer
- Company registration
- Company verification
- Recruiter invitations

### Job Seeker Features

#### Dashboard
Displays:
- Profile completion
- Recent applications
- Saved jobs
- Recommended jobs
- Notifications

#### Profile
- Personal information
- Professional headline
- Bio
- Skills
- Languages
- Education
- Work experience
- Certifications
- Portfolio links
- Salary expectation
- Preferred work location
- Employment preference (Remote, Hybrid, On-site)

#### Resume
- Upload PDF/DOCX
- Set default resume
- Resume version history

#### Job Search
Search using:
- Keyword
- Company
- Location
- Salary range
- Industry
- Experience level
- Employment type
- Remote/Hybrid/On-site

#### Applications
- Apply in one click
- Track application status
- Withdraw application
- View interview invitations

#### Saved Jobs
- Bookmark jobs for later

### Employer Features

#### Company Profile
- Logo
- Description
- Website
- Industry
- Company size
- Headquarters
- Social links

#### Job Management
- Create jobs
- Edit jobs
- Publish jobs
- Pause jobs
- Close jobs
- Duplicate jobs

#### Applicant Management
View:
- Applicants
- Resume
- Cover letter
- Application timeline

Actions:
- Shortlist
- Reject
- Schedule interview
- Send offer

#### Recruiter Pipeline
```
Applied
   ↓
Under Review
   ↓
Shortlisted
   ↓
Interview
   ↓
   Offer
   ↓
  Hired
   ↓
Rejected
```

#### Notifications
- Email
- In-app notifications
- Interview reminders
- Application updates

### Admin Panel

#### User Management
- Suspend users
- Verify companies
- Verify recruiters
- View reports

#### Job Moderation
- Approve jobs (optional)
- Remove fake jobs
- Flag suspicious employers

#### Analytics
- New users
- Active jobs
- Applications
- Revenue
- Verified companies

### Search Filters
- Country
- State
- City
- Remote
- Hybrid
- On-site
- Salary
- Experience
- Job type
- Industry
- Company
- Date posted

### Job Categories
- Software Engineering
- Product Management
- UI/UX Design
- Data & AI
- Finance
- Banking
- Healthcare
- Education
- Government
- Agriculture
- Construction
- Oil & Gas
- Manufacturing
- Hospitality
- Logistics
- Customer Support
- Sales
- Marketing
- Human Resources
- Legal
- Security
- Retail
- Graduate Programs
- Internships
- Freelance
- Contract

## Subscription Plans (MVP)

### Free Employer
- Limited active jobs
- Basic applicant management

### Professional
- More job postings
- Advanced filtering
- Recruiter collaboration
- Company branding

### Enterprise
- Unlimited jobs
- Team management
- Advanced analytics
- Priority support
- API access (future)

## Revenue Model

### Employers
- Monthly subscriptions
- Featured job listings
- Sponsored company profiles
- Job posting credits

### Job Seekers (Optional)
- Resume review
- Career coaching
- Priority profile visibility

## Trust & Safety
- Company verification
- Recruiter verification
- Email verification
- Scam reporting
- Duplicate account detection
- Spam filtering

## AI Features (Post-MVP)

AI should enhance the platform—not define it.

Examples:
- Resume analysis
- Resume scoring
- Job recommendations
- Candidate recommendations
- Interview question generation
- Salary estimation
- Cover letter assistance

## Future Roadmap

### Recruitment
- Video interviews
- Coding assessments
- Aptitude tests
- Psychometric testing

### HR
- Employee onboarding
- Payroll integration
- Attendance management
- Leave management

### Enterprise
- ATS automation
- Background checks
- Digital offer signing
- HRIS integrations

### Universities
- Campus recruitment
- Student placement
- Internship portal

## Recommended Technology Stack

### Frontend
- Next.js
- TypeScript
- Tailwind CSS
- TanStack Query
- React Hook Form
- Zod

### Mobile
- React Native (later)

### Backend
- NestJS
- TypeScript

### ORM
**TypeORM**

Chosen because it offers:
- Excellent NestJS integration
- Mature ecosystem
- Strong support for complex relationships
- Robust transaction management
- Migrations and repositories
- Well suited to enterprise applications with rich relational models

### Database
- PostgreSQL

### Cache
- Redis

### Background Jobs
- BullMQ
- Redis

### Search
- PostgreSQL Full-Text Search (MVP)
- OpenSearch or Elasticsearch (at scale)

### Storage
- Cloudflare R2 (recommended)
- Amazon S3
- MinIO (development)

### Authentication
- JWT
- Refresh Tokens
- Google OAuth
- Email Verification
- Two-Factor Authentication (optional)

### Payments
- Paystack
- Flutterwave
- Stripe (future global expansion)

### Real-time
- WebSockets
- Socket.IO

### Email
- Resend
- Amazon SES (future)

### SMS
- Termii
- Twilio (future)

### Deployment
- Docker
- Kubernetes (when scaling)
- Cloudflare
- AWS / Azure / Google Cloud

## Database Design

Use UUIDs as primary keys for all entities.

Every table should include:
- `id`
- `createdAt`
- `updatedAt`
- `deletedAt` (soft delete)
- `createdBy` (where applicable)
- `updatedBy` (where applicable)

### Core Entities
- Users
- Roles
- Permissions
- Companies
- Recruiters
- Jobs
- Applications
- Resumes
- Skills
- UserSkills
- Education
- Experience
- SavedJobs
- Notifications
- Subscriptions
- Payments
- AuditLogs

## Performance & Scalability

- Use indexes on frequently queried fields such as `email`, `companyId`, `jobId`, `status`, `location`, `employmentType`, `experienceLevel`, and `createdAt`.
- Store resumes and media files in object storage rather than PostgreSQL.
- Cache frequently accessed data (job searches, company profiles, popular listings) with Redis.
- Process emails, notifications, and other long-running tasks asynchronously with BullMQ.
- Begin with PostgreSQL Full-Text Search and adopt OpenSearch or Elasticsearch when search volume and complexity increase.

## Long-Term Vision

The platform should evolve from a traditional job board into a comprehensive hiring operating system that enables organizations to attract talent, manage recruitment, collaborate internally, make hiring decisions, and eventually onboard employees—all from a single platform. This creates stronger customer retention, multiple recurring revenue streams, and a sustainable competitive advantage.
