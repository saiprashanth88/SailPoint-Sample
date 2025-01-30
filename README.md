**IdentityIQ Implementation Project**

Overview

This project involves the installation, configuration, and implementation of SailPoint IdentityIQ to manage identity governance and access control. The setup includes integrating various data sources, automating provisioning workflows, implementing role-based access control (RBAC), and configuring attestation processes.

**Technologies Used**

IdentityIQ (Latest version)

Tomcat 9.0

MySQL 8.0

CentOS 7.9

OpenJDK 11.0.11

OpenLDAP (Enterprise Directory)

OrangeHR (HR System & HR Self Service)

Features Implemented

1. IdentityIQ Installation & Security

Installed IdentityIQ on CentOS with Tomcat and MySQL

Configured IdentityIQ authentication using LDAP credentials (uid-based login)

Customized look and feel with corporate logo and colors

Implemented internal access controls to limit dashboard functionality

Configured audit logging for key events (email logs, triggered events)

2. Data Loading & Integration

Integrated HR System (OrangeHR) via JDBC connector with authoritative data source

Integrated Enterprise Directory (OpenLDAP) for user provisioning

Integrated HR Self Service (OrangeHR) for self-service management

Configured data aggregation & correlation mechanisms

Scheduled data loading:

HR & Enterprise Directory updates: Every 120 mins

Full HR data load: Every Sunday at 2 AM CT

Full Enterprise Directory load: Every 60 mins

HR Self Service update: Weekly at 2 AM CT

3. Automated Provisioning

Implemented Joiner Workflow:

New users detected in HR are automatically provisioned

Role-based provisioning based on department attribute

Generated Enterprise Directory passwords (secure format)

Assigned VPN group membership for remote access

Created HR Self Service accounts

Sent HTML-based welcome email notifications

Implemented Leaver Workflow:

Users marked as terminated are disabled immediately

Accounts moved to Terminated OU after 90 days

HR Self Service accounts deleted after 90 days

4. Role-Based Access Control (RBAC)

Assigned birthright roles based on department

Configured predefined Enterprise Directory groups for:

Engineering (dir-admin_net, xcl-user_app, wrd-user_app)

Tool Design (cck-admin_app, mysql-admin_app, xcl-user_app)

General Employees (vpn-corp_ssl)

5. Access Request & Approval

Configured self-service access request for:

Enterprise Directory entitlements

HR Self-Service roles

Approval workflow:

Manager approval required

Secondary approval for specific entitlements

Automated reminder notifications (3, 6, and 9-day escalation)

6. Attestation & Compliance

Manager Access Reviews: Every 6 months

High Visibility Reviews: Multi-level attestation for high-risk access

Customization of attestation UI:

Removed Risk Score & "Change Detected"

Added Employee ID to attestation reports

7. Preferred Attribute Change Form

Implemented a dashboard-accessible Preferred Name Change Form

Restricted access to managers only

Allowed editing of key LDAP attributes (cn, uid, mail, givenName, etc.)

Audited all changes with requester details
