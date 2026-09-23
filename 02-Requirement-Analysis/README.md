# Phase 2 – Requirement Analysis

## Project Title

Implement Client Script & UI Policy (Incident)

## Platform

ServiceNow

## Module

Incident Management

## 1. Functional Requirements

The system should provide the following functions:

1. The system should apply a UI Policy when Incident Impact is High.

2. The Urgency field should become read-only when Impact is High.

3. When Impact changes to High, Urgency should automatically be set to High.

4. The system should prevent saving a High Impact Incident when Assigned To is empty.

5. The system should display an error message when Assigned To is missing.

6. The system should prevent State changes through direct list editing.

7. State changes should be allowed when the Incident is opened through the form.

8. UI Policy behavior should be reversed when the Impact condition is no longer satisfied.

## 2. Non-Functional Requirements

- The solution should be easy to use.
- The configuration should work within the ServiceNow Incident module.
- The validation should provide clear messages to users.
- The solution should maintain data consistency.
- The client-side controls should respond dynamically to user actions.

## 3. Software Requirements

- ServiceNow Instance
- Web Browser
- JavaScript
- GitHub

## 4. User Requirements

Users should be able to create and update Incident records while following the defined business rules.

The system should guide users when required information is missing and prevent invalid submissions.

## 5. Business Rules

### Rule 1 – High Impact

When Impact is High, additional controls should be applied.

### Rule 2 – Urgency

Urgency should automatically be set to High when Impact is High.

### Rule 3 – Assigned To

Assigned To must be provided before submitting a High Impact Incident.

### Rule 4 – State

State should not be changed directly through list editing.

## 6. Expected Outcome

The requirements will ensure that Incident records contain valid and consistent information while providing appropriate field behavior and validation to users.
