# Leave-Approval-System
The Leave Approval System is a ServiceNow application that automates employee leave requests. Employees submit leave online, dates are validated, requests are sent to managers for approval using Flow Designer, status updates automatically, and notifications are sent. The system reduces paperwork and improves efficiency.

Features
Employee Leave Request Form
Multiple Leave Types
Date Validation using Business Rule
Manager Approval using Flow Designer
Automatic Status Update
Email/Notification Support
Leave Request Tracking
User Roles (Admin & Employee)
Secure Access Control
Technologies Used
ServiceNow Studio
Flow Designer
Business Rules
Tables & Forms
Access Control (ACL)
Notifications
GitHub / GitLab Source Control
Workflow
Employee Login
       │
       ▼
Open Leave Approval Application
       │
       ▼
Fill Leave Request Form
(Employee, Leave Type,
Start Date, End Date, Reason)
       │
       ▼
Business Rule Validation
(Is End Date ≥ Start Date?)
       │
 ┌─────┴─────┐
 │           │
Invalid     Valid
 │           │
Show Error   Save Record
             │
             ▼
Status = Pending
             │
             ▼
Flow Designer Trigger
(Record Created)
             │
             ▼
Manager Approval
             │
      ┌──────┴──────┐
      │             │
Approve        Reject
      │             │
      ▼             ▼
Update Status   Update Status
Approved        Rejected
      │             │
      ▼             ▼
Send Email/     Send Email/
Notification    Notification
      │             │
      ▼             ▼
Employee Views Final Status
Modules
Employee
Apply Leave
View Leave Status
View Leave History
Manager
Approve Leave
Reject Leave
View Pending Requests
Administrator
Manage Users
Manage Leave Types
Configure Workflow
Manage Notifications
Database Design
Leave Request Table
Field	Type
Employee	Reference (sys_user)
Leave Type	Choice
Start Date	Date
End Date	Date
Reason	String
Status	Choice
Business Rule

Name: Validate Dates

Purpose:
Prevent users from entering an end date earlier than the start date.

Flow Designer

Trigger

Record Created

Table

Leave Request

Actions

Ask for Manager Approval
Wait for Approval
If Approved
Update Status = Approved
Send Notification
Else
Update Status = Rejected
Send Notification
Expected Output
Employee submits a leave request.
Status changes to Pending.
Manager receives an approval request.
Manager approves or rejects the request.
Status updates automatically.
Employee receives a notification.
Leave history is stored for future reference.
