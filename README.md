# TaiGer Portal

The project of TaiGer portal will increase the efficiency of files exchange and communication between editor, agent and students. With a great overview, agent and editor can follow up the application process of each student. Furthermore, it opens a bunch of opportunities to extend the service to students like transcript-analysis.

The production link: https://taigerconsultancy-portal.com/

## Technology Overview

TaiGer portal is implemented by JavaScript framework ExpressJS as backend to serve API requsts and ReactJS as frontend. MongoDB stores all user data. Special service like Transcript-Analysis is implemented in Python.

## Architecture:

![](https://github.com/LIYUNG/TaiGer_Portal_Arch/raw/main/architecture.drawio.png)


### Backend
- Express JS in Javascript
- JWT cookie authentication via `passport`
- MongoDB for programs, user information, applications, documents, messages and more.
  
### Frontend
- React in Javascript
- Material-UI library with responsive design
- Use tanstack `react-query` as frontend API client. Optimize API call and caching for better UX.

### Infrastructure
- AWS S3 Bucket for business data storage
- AWS S3 + Cloudfront for frontend website hosting
- AWS EC2 for nodejs backend server (migrating to AWS ECS Fargate for CICD in the future)
- AWS Cloudwatch monitoring EC2
- AWS SES for notification
- AWS Route53 for domain name hosted zone management

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