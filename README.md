# TaiGer Portal

The project of TaiGer portal will increase the efficiency of files exchange and communication between editor, agent and students. With a great overview, agent and editor can follow up the application process of each student. Furthermore, it opens a bunch of opportunities to extend the service to students like transcript-analysis.

The production link: https://taigerconsultancy-portal.com/

## Technology Overview

TaiGer portal is implemented in TypeScript end to end: an ExpressJS backend serving the API and a React + Vite frontend. MongoDB (via Mongoose) stores the core business data, with Drizzle ORM over PostgreSQL for relational data. Special services like Transcript-Analysis are implemented in Python and integrated as microservices.

## Architecture:

![](https://github.com/LIYUNG/TaiGer_Portal_Arch/raw/main/architecture.drawio.png)


### Backend
- Express 4 in TypeScript (Node 20), run with `ts-node` in dev and compiled with `tsc` for production
- JWT cookie authentication via `passport` (`passport-jwt`, `passport-local`), password hashing with `bcryptjs`
- MongoDB via `mongoose` for programs, users, applications, documents, messages and more; Drizzle ORM over PostgreSQL (`pg`) for relational data
- AWS SDK v3 clients for S3, SES/SESv2 and STS
- AI integrations via `@anthropic-ai/sdk` and `openai`
- File handling with `multer` / `multer-s3`, `mammoth`, `pdf-parse`, `jspdf` and `easy-template-x`
- Scheduled jobs with `node-schedule`, email via `nodemailer`, calendar invites via `ical-generator`
- Security & hardening with `helmet`, `cors`, `compression` and `express-rate-limit`
- Tested with Jest + Supertest, linted with ESLint and formatted with Prettier

### Frontend
- React 18 in TypeScript, bundled with Vite
- Material-UI (MUI v5) with `x-data-grid`, `x-charts` and `x-date-pickers` for responsive, data-rich UI
- Tanstack `react-query` as the API client for request de-duplication and caching, plus `react-form` for forms
- Redux (`react-redux`) for global state
- Editor.js rich-text editing, `material-react-table` for sortable/searchable tables, `react-pdf` for document previews
- `react-big-calendar` for appointment booking and `i18next` / `react-i18next` for Mandarin & English localization
- HTTP via `axios`, tested with Vitest + Testing Library

### Infrastructure
All cloud resources are provisioned as code with the **AWS CDK** (TypeScript), split into per-service repos with isolated `dev` and `prod` stages.

**Backend hosting**
- Containerized Node.js API on **AWS ECS Fargate** (ARM64/Graviton), fronted by an Application Load Balancer and exposed through **Amazon API Gateway** on a custom domain
- Runs in a dedicated VPC across two Availability Zones with target-tracking auto-scaling on CPU
- Docker images in **Amazon ECR** (scan-on-push + cross-region replication); runtime config and secrets pulled from **AWS Secrets Manager**
- Blue/green rollouts via **AWS CodeDeploy** with a `/health` check

**Frontend hosting**
- React build served as a static site from a private **S3** bucket via **CloudFront** (Origin Access Control), with **Lambda@Edge** for SPA routing and request handling
- CloudFront routes API/auth paths to the API Gateway origin; access logs retained in S3

**Data, messaging & DNS**
- **S3** for business document storage
- **MongoDB** for application data and **PostgreSQL** for relational data
- **Amazon SES** for transactional email and notifications
- **Amazon Route 53** for DNS and **ACM** for TLS certificates

**Observability**
- Centralized **CloudWatch** logs and metrics with per-stage dashboards

**CI/CD**
- Fully automated **CDK Pipelines** (CodePipeline v2) triggered from GitHub
- Backend: unit tests → Docker build (Graviton) → CDK synth → deploy
- Frontend: unit tests → Vite build → S3 sync → CloudFront invalidation
- Manual approval gate before every production deployment

### Other Microservice dependencies
- Course Analyzor AWS Lambda Proxy (TaiGer)
- AI intelligent program recommender (Tenfold AI)


### Features
- Student course transcript analysis for universities' requirements.
- Email notification for application deadline, new messages, reminder
- Document exchanges between students and TaiGer staff
- AI agent integration (in progreess)
- Language localization (Mandarin and English)
- Appointment booking system
- Internal dashboard and data visualization charts for better overview of the customers' data.
- Document preview, approve, reject, comments.
- and more with CRM features in progress.
 
### Screenshots Demonstration

#### Dashboard
Overview of all students, applications, documents status need attention etc.

![](/screenshots/dashboard.png)

#### Document Previews

With check list, so that we make sure what student uploaded are valid documents for the application

![](/screenshots/document-preview.png)


#### Messages

![](/screenshots/messages.png)

#### Applications Overview

![](/screenshots/applications-overview.png)


#### Find programs

![](/screenshots/program-list.png)

#### Student Dashboard

![](/screenshots/student-dashboard.png)

#### Internal Dashboard

![](/screenshots/internal-dashboard.png)

#### Student's course Analysis report
Based on student's transcript and credits earn, a quantitative analysis can be performed according to the requirements from the study programs which publish their detailed requirements.

![](/screenshots/Course_analysis_report_page.png)

#### Student applications progress

![](/screenshots/student_applications_progress_page.png)

### Student tasks management table (Sortable, searchable)
This make editor's life easier to check and modify studen't documents like essay, statement of purpose etc. as per urgency or deadline.
![](/screenshots/task_management_table.png)