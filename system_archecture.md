# System Architecture

## 1. Business Design

Before configuring HubSpot, the business model and customer lifecycle were defined.

### Business

RenewGrid is a simulated renewable-energy company providing solar-powered electricity services to rural communities and peri-urban commercial customers.

### Communities

The CRM includes six service communities:
* Emina
* Ivara
* Havil
* Farana
* Dantia
* Kelani
* Departments

### Departments

* Customer Experience
* Finance
* Operations
* Human Resources

The CRM primarily supports Customer Experience, Finance, and Operations workflows.

### Customer Types

Customers are segmented into:

* Residential
* Small Business
* Commercial

RenewGrid's core offering is solar-powered electricity service delivered through different tariff plans based on customer requirements.

### Tarriff Plans

* Residential Basic
* Residential Plus
* SME Basic
* SME Plus
* Commercial Standard
* Commercial Premium


## 2. CRM Architecture

The HubSpot environment was configured around the major CRM objects and operational requirements.

### Contacts

Customer records contain information such as:

* Customer ID
* Name
* Email
* Phone
* Meter Number
* Community
* Customer Type
* Tariff Plan
* Installation Date
* Meter Status
* Service Status
* Subscription Expiry Date
* Last Recharge Date
* Customer Health Status

### Deals

Deals represent the customer acquisition journey.

The acquisition pipeline follows the progression from prospective customer to activation.

```
New Lead
   ↓
Qualified
   ↓
Registration Completed
   ↓
Payment Pending
   ↓
Installation Scheduled
   ↓
Installation Completed
   ↓
Activated
   ↓
Closed Lost
```

This allows the organization to monitor where prospective customers are in the acquisition process.


### Tickets

Tickets represent customer support and service issues.

Categories include:

* Power Outage
* Meter Fault
* Low Voltage
* Payment Issue
* Wrong Billing
* New Connection
* Relocation**
* Technical Complaint
* General Enquiry

This separates operational support activity from the customer's general CRM record.


## 3. Customer Data Collection

A customer registration form was created to simulate the initial customer acquisition process.

The form captures key customer information and feeds the CRM contact database.

A synthetic dataset of 50 customer records was created for testing.

The dataset was validated before being imported into HubSpot.

Validation included checks for:

* Missing values
* Duplicate records
* Invalid dates
* Inconsistent customer classifications
* Inconsistent tariff assignments
* Community naming inconsistencies
* Invalid or incomplete contact information

Identified data-quality issues included:

* duplicate email records;
* an invalid calendar date;
* a customer type and tariff mismatch;
* inconsistent community capitalization.

The records were reviewed, validated, corrected, and imported into HubSpot.


## 4. Customer Onboarding Automation

The first major automation addresses the transition from registration to onboarding.

Trigger

A customer enters the CRM with a pending activation status.

Automated actions

```
New Customer
     ↓
Assign Customer Owner
     ↓
Send Welcome Email
     ↓
Create Onboarding Task
     ↓
Follow-Up
```

### Operational benefit

This reduces manual administrative work and creates a consistent onboarding experience.

Instead of relying on a team member to remember every new registration, the CRM automatically initiates the required actions.


## 5. Subscription Management

RenewGrid includes an automated subscription-expiry process.

### Business rule

Customers approaching subscription expiry should receive timely communication and internal follow-up.

```
Subscription Expiry Approaching
            ↓
Renewal Reminder
            ↓
Internal Notification
            ↓
Follow-Up Task
```

### Operational benefit

This helps reduce missed renewal opportunities and allows Customer Experience teams to intervene before service disruption occurs.


## 6. 48-Hour Escalation

To prevent unresolved issues from remaining unattended, RenewGrid implements a 48-hour escalation rule.

```
Ticket Created
      ↓
Wait 48 Hours
      ↓
Still Unresolved?
    /       \
  YES        NO
   ↓          ↓
Escalate     Close
   ↓
Increase Priority
   ↓
Notify Supervisor
   ↓
Create Escalation Task
```

### Operational benefit

The process introduces accountability and reduces the risk of support tickets becoming forgotten backlog items.


## 7. Support Operations

Customer complaints are managed through HubSpot Tickets. A power-outage complaint triggers an automated support process.

```
Power Outage Complaint
          ↓
High Priority
          ↓
Technical Team
          ↓
Customer Acknowledgement
          ↓
Operations Notification
```

This creates a structured response path from customer complaint to technical intervention.


## 8. Customer Retention

Customer inactivity is treated as a potential early warning signal. The CRM identifies customers who have not recharged for an extended period.

### Re-engagement process

```
No Recharge for 30+ Days
          ↓
Customer Health = At Risk
          ↓
Re-engagement Email
          ↓
Customer Success Notification
          ↓
Follow-Up Call Task
```

The purpose is not simply to classify customers as inactive, but to create an intervention process around the signal.

## 9. Customer Health

Customer Health Status provides a high-level view of customer relationship risk.

Customers can be classified based on operational signals such as:

* Recharge activity
* Service status
* Support history
* Subscription status
* Customer feedback

This enables Customer Success teams to prioritize intervention instead of treating every customer identically.


## 10. Customer Experience & CSAT

When a support ticket is resolved, the customer is invited to provide feedback.

```
Ticket Closed
     ↓
CSAT Survey
     ↓
Customer Response
     ↓
Satisfaction Evaluation
     ↓
Low Score?
   /    \
 YES     NO
  ↓       ↓
Escalate  Thank Customer
  ↓
Follow-Up Task
  ↓
Supervisor Notification
```

Low customer satisfaction responses trigger additional attention. This creates a feedback loop between:

> Support → Customer Feedback → Improvement


## 11. Analytics

Three role-specific dashboards were designed.

### Executive Dashboard

Provides management-level visibility into:

* Total customers
* Customer status
* Customer health
* Customer mix
* Customers by community
* Open support issues
* Ticket priorities

### Operations Support Dashboard

Focuses on:

* Open tickets
* Ticket categories
* Ticket priority
* Escalated tickets
* Resolution performance


### Customer Success Dashboard

Focuses on:

* Active customers
* At-risk customers
* Inactive customers
* Customer health Distribution
* Customers by Community


## 12. Data & Assumptions

All customer information used in this project is synthetic.

The dataset was created specifically to simulate realistic CRM operations without exposing personal customer information.

Operational test records were also created to demonstrate:

* Customer acquisition
* Support tickets
* Escalations
* Subscription events
* Customer inactivity
* Customer feedback

Where real email delivery or customer interaction was required for testing, controlled test accounts were used.
