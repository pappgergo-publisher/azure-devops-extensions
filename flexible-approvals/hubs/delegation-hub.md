# Delegation hub

**In this article**
- [Usage](#usage)
- [Actions](#actions)
- [Filtering](#filtering)
- [Disabling](#disabling)
- [See also](#see-also)

Show approver delegations and allow actions on them. 

## Usage

There are 3 different delegation pages: organization, project, own. 
They are located at a different place, use a different list of approver delegations and allow different actions.

### Organization

**Approver delegations:** every approver delegations in the organization   
**Actions:** cancel, delete   
**Location**: under the `Organization settings` hub group

![Organization hub](/flexible-approvals/images/hubs/delegation-hub/organization-hub.png)

### Project

**Approver delegations:** every approver delegations with organization or current project scope   
**Actions:** cancel, delete   
**Location**: under the `Project settings` hub group

![Project hub](/flexible-approvals/images/hubs/delegation-hub/project-hub.png)

### Own - My delegates

**Approver delegations:** every approver delegations with organization or current project scope having the current user as delegator   
**Actions:** add, cancel   
**Location**: under the `Pipelines` hub group (using the `My delegates` tab)

![Own hub](/flexible-approvals/images/hubs/delegation-hub/own-hub.png)

![My delegates](/flexible-approvals/images/hubs/delegation-hub/my-delegates.png)

### Own - My delegators

**Approver delegations:** every approver delegations with organization or current project scope having the current user as delegator   
**Actions:** none   
**Location**: under the `Pipelines` hub group (using the `My delegators` tab)

![Own hub](/flexible-approvals/images/hubs/delegation-hub/own-hub.png)

![My delegators](/flexible-approvals/images/hubs/delegation-hub/my-delegators.png)

## Actions

**Cancel**

Cancel inactive and active approver delegations.
Cancelling means changing the delegation state to cancelled which prevents excludes the delegation from delegate calculations.

This action can only be used by
- members of the Project Collection Administrators group in the organization hub
- members of the current project's Project Administrator group in the project hub
- the current user in the own hub

**Delete**

Delete approver delegations without any references to them.
Deleting permanently removes the approver delegations, there's no way to restore them!

This action is meant as a tool for cleanup, thus it can only be used by
- members of the Project Collection Administrators group in the organization hub
- members of the current project's Project Administrator group in the project hub

**Add**

Create new approver delegations.
It is required to set the delegation name, the delegates and 
it is possible to fine-tune the scope, the start and end times.

This action is only available to the current user on the own hub's my delegates tab,
thus delegations cannot be created in other people's name.

## Filtering

The delegation hub allows filtering of the presented approver delegations.
For the description of the individual filters, please check [Filtering](/flexible-approvals/common/filtering.md#approver-delegations).

## Disabling

It is possible to disable the delegation hub pages on these levels:
- organization hub: organization
- project hub: organization, project
- own hub: organization, project, personal

For the details, please see the [Extension features](/flexible-approvals/common/extension-features.md).

## See also

- [Filtering](/flexible-approvals/common/filtering.md)
- [Extension features](/flexible-approvals/common/extension-features.md)
- [Glossary](/flexible-approvals/common/glossary.md)