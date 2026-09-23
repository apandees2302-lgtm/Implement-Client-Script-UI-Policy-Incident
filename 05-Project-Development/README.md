# Phase 5 – Project Development

## Project Title

Implement Client Script & UI Policy (Incident)

## Platform

ServiceNow

## Module

Incident Management

## 1. UI Policy Implementation

### UI Policy Name

High Impact Control

### Table

Incident

### Condition

Impact is 1 - High

### Configuration

The UI Policy is activated when the Impact field is set to High.

The policy is configured with Reverse if false so that the field behavior is restored when the condition is no longer true.

## 2. UI Policy Action

### Field

Urgency

### Configuration

Read-only: True

Visible: No change

When Impact is High, the Urgency field becomes read-only.

When Impact changes to another value, the UI Policy behavior is reversed.

## 3. onChange Client Script

### Name

Auto set urgency for high impact

### Table

Incident

### Type

onChange

### Field

Impact

### Script

function onChange(control, oldValue, newValue, isLoading) {
    if (isLoading || newValue == '') {
        return;
    }

    if (newValue == '1') {
        g_form.setValue('urgency', '1');
        g_form.addInfoMessage(
            'Urgency set to High for High impact incident.'
        );
    }
}

### Function

When Impact is changed to High, the script automatically sets Urgency to High.

## 4. onSubmit Client Script

### Name

Prevent save if Assigned To missing

### Table

Incident

### Type

onSubmit

### Script

function onSubmit() {
    if (g_form.getValue('impact') == '1' &&
        g_form.getValue('assigned_to') == '') {

        g_form.showErrorBox(
            'assigned_to',
            'Assigned To is mandatory for High impact incidents.'
        );

        return false;
    }

    return true;
}

### Function

The script prevents submission when the Incident has High Impact and the Assigned To field is empty.

If Assigned To is filled, the Incident can be submitted successfully.

## 5. onCellEdit Client Script

### Name

Prevent state change via list edit

### Table

Incident

### Type

onCellEdit

### Field

State

### Script

function onCellEdit(sysIDs, table, oldValues, newValue, callback) {

    alert(
        'State cannot be updated using list editing. Please open the Incident.'
    );

    callback(false);
}

### Function

The script prevents users from changing the State directly through list editing.

State changes can be performed by opening the Incident record and updating it through the form.

## 6. Development Result

The ServiceNow Incident configuration was implemented using:

- One UI Policy
- One UI Policy Action
- One onChange Client Script
- One onSubmit Client Script
- One onCellEdit Client Script

These configurations work together to control Incident field behavior, automate values, validate submissions, and restrict direct list editing.
