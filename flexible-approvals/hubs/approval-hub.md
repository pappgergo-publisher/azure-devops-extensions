# Approval hub

**In this article**
- [Usage](#usage)
- [Actions](#actions)
- [Filtering](#filtering)
- [Disabling](#disabling)
- [See also](#see-also)

Show approval requests and allow actions on them. 

## Usage

There are 3 different approval pages: organization, project and own. 
They are located at a different place, use a different list of approval requests and allow different actions.

### Organization

**Approval requests:** every approval requests in the organization   
**Actions:** cancel, delete   
**Location**: under the `Organization settings` hub group

![Organization hub](/flexible-approvals/images/hubs/approval-hub/organization-hub.png)

### Project

**Approval requests:** every approval requests in the current project   
**Actions:** cancel, delete   
**Location**: under the `Project settings` hub group

![Project hub](/flexible-approvals/images/hubs/approval-hub/project-hub.png)

### Own

**Approval requests:** every approval requests in the current project having the current user as approver or voter
(delegates are only included for waiting approval requests)   
**Actions:** approve, reject   
**Location**: under the `Pipelines` hub group

![Own hub](/flexible-approvals/images/hubs/approval-hub/own-hub.png)

## Actions

**Cancel**

Cancel new and waiting approval requests whose pipeline run is already completed.
Cancelling means changing the approval request state to cancelled which prevents casting additional votes.

This action is meant as a tool for cleanup, thus it can only be used by
- members of the Project Collection Administrators group in the organization hub
- members of the current project's Project Administrator group in the project hub

**Delete**

Delete approval requests whose pipeline run is already deleted.
Deleting permanently removes the approval requests, there's no way to restore them!

This action is meant as a tool for cleanup, thus it can only be used by
- members of the Project Collection Administrators group in the organization hub
- members of the current project's Project Administrator group in the project hub

**Approve**

Cast approved vote to approval requests.
For more details on this, please check [Casting votes](/flexible-approvals/common/casting-votes.md).

**Reject**

Cast rejected vote to approval requests.
For more details on this, please check [Casting votes](/flexible-approvals/common/casting-votes.md).

## Filtering

The approval hub allows filtering of the presented approval requests.
For the description of the individual filters, please check [Filtering](/flexible-approvals/common/filtering.md).

## Disabling

It is possible to disable the approval hub pages on these levels:
- organization hub: organization
- project hub: organization, project
- own hub: organization, project, personal

For the details, please see the [Extension features](/flexible-approvals/common/extension-features.md#approval-requests).

## See also

- [Casting votes](/flexible-approvals/common/casting-votes.md)
- [Filtering](/flexible-approvals/common/filtering.md)
- [Extension features](/flexible-approvals/common/extension-features.md)
- [Glossary](/flexible-approvals/common/glossary.md)