# Phase 3 – Project Design

## Project Title

Implement Client Script & UI Policy (Incident)

## Platform

ServiceNow

## Module

Incident Management

## 1. System Design

The project is designed using ServiceNow client-side configuration.

The Incident table is controlled using UI Policies and Client Scripts.

## 2. UI Policy Design

### UI Policy Name

High Impact Control

### Table

Incident

### Condition

Impact is 1 - High

### Behavior

When Impact is High, the UI Policy is triggered.

The UI Policy controls the behavior of Incident fields.

## 3. UI Policy Action Design

### Field

Urgency

### Action

Read-only = True

When Impact is High, the Urgency field cannot be modified by the user.

When the condition becomes false, the UI Policy behavior is reversed.

## 4. Client Script Design

### onChange Client Script

The onChange Client Script monitors the Impact field.

When Impact is changed to High, the script automatically sets Urgency to High.

### onSubmit Client Script

The onSubmit Client Script validates the Assigned To field.

If Impact is High and Assigned To is empty, the Incident cannot be submitted.

### onCellEdit Client Script

The onCellEdit Client Script controls State changes made directly from the Incident list.

It prevents users from changing State through list editing.

## 5. Process Flow

1. User opens or creates an Incident.
2. User selects an Impact value.
3. If Impact is High, the UI Policy becomes active.
4. Urgency becomes read-only.
5. The onChange Client Script sets Urgency to High.
6. When the user submits the Incident, the onSubmit Client Script checks Assigned To.
7. If Assigned To is empty, submission is prevented.
8. If Assigned To is available, the Incident is saved.
9. Direct State changes from list editing are blocked by the onCellEdit Client Script.

## 6. Design Outcome

The design provides dynamic field control, automatic value updates, form validation, and list-edit restrictions for Incident records.

The design ensures that the Incident form follows the required business rules before records are submitted.
