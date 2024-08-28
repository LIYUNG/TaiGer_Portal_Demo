# TaiGer Portal

The project of TaiGer portal will increase the efficiency of files exchange and communication between editor, agent and students. With a great overview, agent and editor can follow up the application process of each student. Furthermore, it opens a bunch of opportunities to extend the service to students like transcript-analysis.

## Technology Overview

TaiGer portal is implemented by JavaScript framework ExpressJS as backend to serve API requsts and ReactJS as frontend. MongoDB stores all user data. Special service like Transcript-Analysis is implemented in Python.

### Backend
- Express in Javascript
- JWT cookie authentication
- MongoDB for programs, user information, applications, documents, messages and more.
  
### Frontend
- React in Javascript
- Material-UI library with responsive design

### Infrastructure
- AWS S3 Bucket for business data storage
- AWS S3 + Cloudfront for frontend website hosting
- AWS EC2 for nodejs backend server
- AWS Cloudwatch monitoring EC2
- AWS SES for notification
- AWS Route53 for domain name hosted zone management

### Features
- Student course transcript analysis for universities' requirements.
- Email notification for application deadline, new messages, reminder
- Document exchanges between students and TaiGer staff
- OpenAI integration 
- Language localization (Madarin and English)
- Appointment booking system
- Internal dashboard and data visualization charts for better overview of the customers' data.
- Document preview
- and more with CRM features.
 
### Screenshots

#### Dashboard
Overview of all students, applications, documents status need attention etc.

![](/screenshots/dashboard.png)

#### Document Previes

With check list, so that we make sure what student uploaded are valid documents for the application

![](/screenshots/document-preview.png)


#### Messages

![](/screenshots/messages.png)

#### Internal Dashboard

![](/screenshots/internal-dashboard.png)