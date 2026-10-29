# automated-equipment-request-system
Automated employee equipment approval system built with Make.com, webhooks, and API integrations.

# Automated Equipment Request & Approval System

**Business Process Automation | Make.com | REST APIs | Webhooks**

## Project Overview

Designed, built, and tested an automated employee equipment request and approval system using Make.com.

The system processes incoming equipment requests, automatically approves low-cost items, and routes higher-cost requests for management review.

This project demonstrates workflow automation, API integration, conditional logic, persistent data storage, troubleshooting, and business process improvement.

## Business Problem

Traditional equipment approval processes often require manual review of every request, regardless of cost.

This can create unnecessary administrative work, delays, and inconsistent decision-making.

The goal was to automate routine approvals while maintaining management oversight for higher-cost purchases.

## Solution Architecture

The system consists of two interconnected Make.com scenarios.

### Workflow 1: Equipment Request Intake

1. Receive employee equipment requests through a custom webhook.
2. Extract employee information, equipment details, and request cost.
3. Evaluate the equipment cost using conditional routing.
4. Automatically approve requests costing $100 or less.
5. Route requests exceeding $100 for manager approval.
6. Store request information in a persistent Data Store.
7. Integrate Gmail for notification handling.

### Workflow 2: Manager Approval Processing

1. Receive an approval or rejection decision through an authenticated webhook.
2. Identify the request using its unique request ID.
3. Retrieve the existing request from the Data Store.
4. Validate that the request is still pending manager approval.
5. Route the decision to the appropriate processing path.
6. Update the request status to Approved or Rejected.
7. Preserve the original employee, equipment, and cost information.

## Technologies Used

| Technology | Purpose |
|---|---|
| Make.com | Workflow orchestration |
| Webhooks | Event-driven request intake |
| REST API / HTTP | Communication between systems |
| JSON | Structured request data |
| Make Data Stores | Persistent request storage |
| Conditional Routers | Business-rule evaluation |
| Gmail | Email notification integration |
| Postman | API testing |
| API Keys | Webhook authentication |

## Business Rules

| Request condition | System behavior |
|---|---|
| Equipment cost ≤ $100 | Automatically Approved |
| Equipment cost > $100 | Pending Manager Approval |
| Manager selects Approved | Update status to Approved |
| Manager selects Rejected | Update status to Rejected |
| Request already finalized | Do not overwrite the decision |
| Invalid request ID | No record update |
| Unsupported decision | No status change |
| Missing or invalid API key | Reject unauthorized request |

## Testing and Validation

The following functional tests were completed successfully:

- Automatic approval of a qualifying low-cost equipment request.
- Manager approval of an existing pending request.
- Manager rejection of an existing pending request.
- Preservation of existing request information after approval updates.
- Prevention of a conflicting decision against an already finalized request.
- Handling of a nonexistent request ID.
- Rejection of unsupported decision values.
- Authentication testing with valid and missing API keys.
- Verification of stored request statuses.

## Security and Reliability

Implemented API-key authentication on the manager decision webhook.

Verified that requests without valid authentication are rejected with HTTP 401 Unauthorized.

Configured sequential processing for manager approval decisions and conditional filters to prevent ordinary repeated decisions from overwriting finalized request statuses.

### Known Limitations

This is a functional portfolio demonstration, not a production-ready purchasing platform.

Additional development would be needed for individual manager identity verification, stronger audit logging, operational monitoring, and comprehensive concurrency and security testing.

## Project Outcomes

Created a working, event-driven automation that:

- Reduces the need for manual review of routine low-cost purchases.
- Applies consistent equipment approval rules.
- Maintains persistent request information.
- Supports both manager approval and rejection.
- Demonstrates API-based integration and automated business logic.

Actual time savings and organizational performance improvements have not been measured.

## Skills Demonstrated

**Workflow Automation:** Designed event-driven processes using Make.com.

**API Integration:** Configured and tested webhook-based communication using JSON and Postman.

**Business Logic:** Implemented conditional routing, approval thresholds, and decision validation.

**Data Management:** Created and updated persistent records using unique identifiers.

**Troubleshooting:** Investigated authentication failures, validated API responses, and inspected execution logs.

**Process Improvement:** Translated a repetitive administrative process into a functioning automation.

## Project Status

**Core functionality completed and tested.**

Both workflow scenarios are saved in Make.com. Continuous operation and production deployment are outside the scope of this portfolio demonstration.
