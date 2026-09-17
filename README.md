# RenewGrid Hubspot CRM and Customer Operations Automation System
A Hubspot-based CRM operating system designed to connect customer onboarding, support, escalation, satisfaction, retention, and re-engagement, while giving management visibility through operational dashboards.
---

## Contents
[Project Overview](#project-overview)

[Business Problem](#business-problem)
[The Solution](#the-solution)

[Project Objectives](#project-objectives)

[Data Design and Validation](#data-design-and-validation)

[Technology Used](#technology-used)

[System Architecture](#system-architecture)

[Customer Lifecycle](#customer-lifecycle)

[Automation Workflows](#automation-workflows)

[Customer Support Operations](#customer-support-operations)

[Customer Health and Retention](#customer-health-and-retention)

[Customer Experience](#customer-experience)

[Analytics and Dashboards](#analytics-and-dashboards)

[Operational Benefits](#operational-benefits)

[Project Limitations](#project-limitations)

[Future Improvements](#future-improvements)

---

## Project Overview

RenewGrid is a fictional renewable-energy company providing solar-powered electricity services to residential, small-business, and commercial customers across rural and peri-urban communities.

The project began with a simple question:

**What happens after a customer becomes a customer?**

A customer may need onboarding, report a power outage, experience a billing or technical issue, require escalation, become inactive, or provide feedback after receiving support.

Managing these activities as separate processes can create gaps between customer information, operational teams, follow-ups, and management visibility.

RenewGrid was designed to address this by connecting the customer lifecycle inside a single CRM environment.

The result is a HubSpot-based customer operations system covering:

**Customer Acquisition → Onboarding → Service → Support → Escalation → Customer Feedback → Re-engagement → Analytics**

---

## Business Problem

Customer information alone does not create an effective customer operation.

A growing renewable-energy business needs processes that answer questions such as:

* Has a newly registered customer been properly onboarded?
* Who is responsible for following up with the customer?
* What happens when a customer reports a power outage?
* Who is notified when a critical complaint is logged?
* What happens when a ticket remains unresolved for 48 hours?
* Which customers may be at risk of becoming inactive?
* Are customers satisfied after receiving support?
* What happens when a customer gives a poor satisfaction score?
* Can management see customer and support activity without manually combining information?

This project was designed around these operational questions rather than around CRM data storage alone.

---

## The Solution

RenewGrid uses HubSpot as the customer relationship and service-management layer for the business.

The system brings together:

* Customer records
* Customer segmentation
* Acquisition opportunities
* Customer onboarding
* Support tickets
* Complaint categorization
* Automated notifications
* Escalation management
* Customer health monitoring
* Re-engagement activities
* Customer satisfaction feedback
* Operational dashboards

The system is designed so that a customer interaction can trigger the next appropriate operational action.

---
## Project Objectives

The system was designed to:

1. Centralize customer information.
2. Create a structured customer lifecycle.
3. Standardize customer onboarding.
4. Automate operational follow-ups.
5. Improve visibility into customer complaints.
6. Introduce time-based ticket escalation.
7. Identify inactive customers for re-engagement.
8. Capture customer feedback after support.
9. Create follow-up actions for low customer satisfaction.
10. Give management role-specific operational visibility through dashboards.

---

## Data Design and Validation
A customer registration form was created to simulate the initial customer acquisition process. The form captures key customer information and feeds the CRM contact database.
View the form [here](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/images/RenewGrid%20Registration%20Form.png)

A synthetic dataset of 50 customer records was created for testing. 
[Click to see the dataset](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/files/RenewGrid_50_Customer_Dataset.xlsx)

The dataset was validated before being imported into HubSpot.

Validation included checks for:

* Missing values
* Duplicate records
* Invalid dates
* Inconsistent customer classifications
* Inconsistent tariff assignments
* Community naming inconsistencies
* Invalid or incomplete contact information

Click [here](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/images/Data%20Quality%20Log.png) to view the data quality log. 

Identified data-quality issues included:

* duplicate email records;
* an invalid calendar date;
* a customer type and tariff mismatch;
* inconsistent community capitalization.

The records were reviewed, validated, and corrected before import.

You can see the cleaned dataset [here](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/files/RenewGrid_Cleaned_Customer_Dataset.xlsx)

### Data Assumptions
All customer information used in this project is synthetic. The dataset was created specifically to simulate realistic CRM operations without exposing personal customer information.

Operational test records were also created to show:

* Customer acquisition
* Support tickets
* Escalations
* Subscription events
* Customer inactivity
* Customer feedback

Where real email delivery or customer interaction was required for testing, controlled test accounts were used.

---

## Technology Used

### CRM

* HubSpot

### Data & Analysis

* Microsoft Excel
* Synthetic CSV datasets

### Automation

* Hubspot Workflows

---
## System Architecture

The CRM was structured around four major operational layers:

```
                    RENEWGRID CRM
                         │
        ┌────────────────┼────────────────┐
        │                │                │
   CUSTOMER DATA    ACQUISITION       SUPPORT
        │                │                │
     Contacts          Deals           Tickets
        │                │                │
        └────────────────┼────────────────┘
                         │
                    AUTOMATION
                         │
        ┌────────────────┼────────────────┐
        │                │                │
    Onboarding       Retention       Escalation
        │                │                │
        └────────────────┼────────────────┘
                         │
                  CUSTOMER EXPERIENCE
                         │
                       CSAT
                         │
                    ANALYTICS
                         │
        ┌────────────────┼────────────────┐
        │                │                │
     Executive        Support        Customer Success
     Dashboard        Dashboard         Dashboard
                         │
                  Acquisition Dashboard
```

| CRM Object | Purpose                                      |
| ---------- | -------------------------------------------- |
| Contacts   | Customer information and customer attributes |
| Deals      | Customer acquisition process                 |
| Tickets    | Customer support and complaint management    |
| Workflows  | Automated operational actions                |
| Dashboards | Management and operational visibility        |

[Click here to view the detailed system architecture](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/doc/system_architecture.md)

---

## Customer Lifecycle

The system was designed around the complete customer journey rather than isolated CRM activities.

```text
Lead
 ↓
Qualified
 ↓
Registered
 ↓
Payment
 ↓
Installation
 ↓
Activation
 ↓
Active Customer
 ↓
Support / Service
 ↓
Resolution
 ↓
Customer Feedback
 ↓
Retention / Re-engagement
```

Each stage creates information that can support the next stage of the customer relationship.

---

## Automation Workflows

Five workflows were implemented to automate key customer operations.

### 1. New Customer Onboarding

#### Business need

A newly registered customer should not depend entirely on manual follow-up to begin the onboarding process.

#### Workflow logic

```text
Customer becomes pending activation
          ↓
Assign customer owner
          ↓
Send welcome email
          ↓
Create onboarding task
          ↓
Wait / follow-up
```

### Operational purpose

The workflow is designed to:

* provide a consistent first communication;
* establish ownership;
* create a clear follow-up action;
* reduce the likelihood of newly registered customers being overlooked.

[Click here to view the New Customer Onboarding Workflow](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/tree/main/images/new_customer_onboarding)


### 2. 48-Hour Ticket Escalation

#### Business need

A ticket that remains unresolved indefinitely can become both an operational and customer-experience risk.

RenewGrid therefore introduces a defined escalation threshold.

#### Workflow logic

```text
Ticket remains unresolved
          ↓
48-hour waiting period
          ↓
Is the ticket still open?
       /          \
     No            Yes
     │              │
     ▼              ▼
   End         Priority → Urgent
                    ↓
             Escalation Status
                    ↓
             Supervisor notified
                    ↓
             Escalation task created
```
#### Operational purpose

The workflow is designed to:

* create accountability for aging tickets;
* make overdue issues visible;
* automatically increase priority;
* notify the appropriate supervisor;
* create a concrete follow-up action.

This transforms escalation from an informal reminder into a defined operational process.

[Click here to view the 48-Hour Ticket Escalation Workflow](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/upload/main/images/48-Hour_ticket_escalation)


### 3. Power Outage Workflow

#### Business need

Power outage complaints require prompt visibility because they directly affect service availability.

When a customer reports a power outage, the complaint should move from a customer report to an operational response.

#### Workflow logic

```text
Power outage complaint logged
          ↓
Ticket identified as Power Outage
          ↓
Priority set to High
          ↓
Technical team assigned
          ↓
Customer receives acknowledgement
          ↓
Issue remains monitored
```

The workflow also works together with the 48-hour escalation process.

If the complaint remains unresolved or open for two days, the priority is changed to Urgent, escalated to management, and a Review Task created.

#### Operational purpose

The workflow is designed to:

* route outage complaints to the appropriate team;
* make the issue visible to operations;
* acknowledge the customer;
* establish a clear response path;
* provide a defined escalation route for unresolved complaints.

[Click here to view the Power Outage Workflow](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/upload/main/images/power_outage_workflow)


### 4. CSAT Workflow

#### Business need

Closing a ticket does not necessarily mean the customer had a good experience.

RenewGrid therefore introduces a feedback loop after support resolution.

#### Workflow logic

```text
Ticket closed
     ↓
CSAT survey sent
     ↓
Customer provides feedback
     ↓
Satisfaction evaluated
     ↓
Low score?
   /      \
 No        Yes
 │          │
 ▼          ▼
End     Follow-up task
             ↓
        Supervisor notified
             ↓
        Customer follow-up
```

For low satisfaction scores, the system creates a follow-up action rather than allowing the feedback to end as a number in a report.

#### Operational purpose

The workflow is designed to:

* measure customer satisfaction;
* identify dissatisfied customers;
* create follow-up actions;
* give supervisors visibility into poor experiences;
* create a feedback-to-action loop.

[Click here to view the CSAT Workflow](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/upload/main/images/csat_workflow)


### 5. Customer Re-engagement Workflow

#### Business need

Customer inactivity can indicate a change in customer needs, service experience, technical issues, payment concerns, or other factors.

RenewGrid therefore uses customer activity information as a trigger for proactive follow-up.

#### Workflow logic

```text
Customer has no recharge activity
for defined period
          ↓
Service is still active
          ↓
Customer Health → At Risk
          ↓
Re-engagement email
          ↓
Customer Experience notified
          ↓
Re-engagement task created
```

#### Operational purpose

The workflow is designed to:

* identify potentially inactive customers earlier;
* flag customers as requiring attention;
* initiate proactive communication;
* give Customer Experience a defined follow-up action;
* support customer retention efforts.

[Click here to view the Re-engagement workflow](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/upload/main/images/customer_re-engagement_workflow)

---

## Customer Support Operations

The support model was designed around structured ticket management.

Each ticket can contain information such as:

* Customer
* Community
* Complaint category
* Priority
* Ticket status
* Escalation status
* Assigned owner
* Resolution information

This creates a consistent path from:

**Customer Complaint → Ticket → Assignment → Response → Escalation → Resolution → Feedback**

Instead of treating customer complaints as isolated messages, the CRM turns them into trackable operational records.

---

## Customer Health and Retention

RenewGrid uses customer health as an operational signal.

The system can identify customers who may require attention based on customer activity and workflow conditions.

For example:

```text
Healthy
   │
   │ reduced activity
   ▼
At Risk
   │
   │ prolonged inactivity
   ▼
Inactive
```

Customers identified as requiring attention can enter the re-engagement process.

This creates a proactive customer-success model rather than waiting for customers to return with another complaint.

---

## Customer Experience

Customer experience is incorporated into the support lifecycle through CSAT.

The system does not stop at:

> Ticket closed.

Instead, the process continues:

> Ticket closed → Customer feedback → Satisfaction assessment → Follow-up where necessary.

This creates a feedback loop between service delivery and customer experience.

---

## Analytics and Dashboards

Three operational dashboards were created.


### 1. Executive Dashboard

Designed to provide a high-level view of the customer operation.

![executive_dashboard](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/images/executive_dashboard/Executive%20Dashboard.png)

[View the full dashboard here](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/tree/main/images/executive_dashboard)

#### Management question

**What is happening across the customer operation?**



### 2. Operations Support Dashboard

Designed around support workload and issue management.

![operations-support-dashboard](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/images/operations_support_dashboard/Support%20Operations%20Dashboard_1.png)

[View the full dashboard here](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/upload/main/images/operations_support_dashboard)

#### Management question

**What customer issues are we handling, how serious are they, and where does attention need to go?**



### 3. Customer Success Dashboard

Designed around customer health, retention, and proactive engagement.
![customer-success-dashboard](https://github.com/Winner-Dimiri/RenewGrid-Hubspot-CRM-and-Customer-Operations-Automation-System/blob/main/images/Customer%20Success%20Dashboard.png)

#### Management question

**Which customers may require attention, and what actions are being taken?**

---

## Operational Benefits

The system is designed to create operational benefits across the customer lifecycle.

| Area                | Operational Benefit                                   |
| ------------------- | ----------------------------------------------------- |
| Customer Data       | Centralized customer information                      |
| Onboarding          | Consistent automated follow-up                        |
| Support             | Standardized complaint management                     |
| Power Outages       | Defined response and notification path                |
| Escalation          | Time-based intervention for unresolved tickets        |
| Customer Success    | Earlier visibility into customers requiring attention |
| Retention           | Structured re-engagement process                      |
| Customer Experience | Feedback loop after support                           |
| Management          | Role-specific operational dashboards                  |

The value of the system is not simply that it sends automated emails.

The value is that **business rules are converted into repeatable operational processes.**

---

## Project Limitations

RenewGrid is a fictional portfolio project.

All customer names, contact information, communities, operational records, tickets, deals, and other business data used in the project are synthetic.

The project demonstrates CRM architecture, workflow logic, data management, customer operations, and reporting concepts. It does not represent the internal systems, processes, customers, or operational data of any real renewable-energy company.

Actual business performance outcomes such as churn reduction, response-time improvement, or revenue growth have not been claimed because the project does not have a real operational baseline against which to measure them.

The dashboards therefore demonstrate **operational visibility and reporting design**, rather than claiming measured business results.

---

## Future Improvements

If implemented in a real renewable-energy business environment, the system could be extended with:

* integration with the company's energy-management platform;
* automated synchronization of service and meter status;
* payment and recharge data integration;
* real-time outage information;
* SLA monitoring;
* advanced customer segmentation;
* automated customer communication across multiple channels;
* predictive customer-risk modelling;
* deeper operational analytics;
* role-based reporting and alerts;
* integration with field-service processes.

HubSpot would function as the customer relationship and service-management layer, while the company's core energy platform would remain the appropriate system of record for operational energy data.

---
This project reflects an interest in designing practical systems that connect technology, data, people, and business processes to improve operational visibility and customer experience.
