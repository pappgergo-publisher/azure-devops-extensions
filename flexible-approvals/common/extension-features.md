# Extension features

**In this article**
- [Features](#features)
- [Disabling](#disabling)
- [See also](#see-also)

Allow selective disabling of the Flexible Approvals extension's capabilities.

## Features

Features or preview features (as the Azure DevOps UI presents it) is a mechanism which makes selective enabling or disabling of certain features. 
Microsoft uses it mostly to introduce preview elements and allow users to opt-in to try them out, or opt-out in case they are unwanted for any reason.

Extensions can use the same features menu and include their capabilities in the list. 
The Flexible Approvals extension does so, which allows you to control what you/your project/your organization want to use and what should be hidden.

## Disabling

By default all features of the extension is turned on.
In case one feature is not needed, it is possible to turn it off on 1, 2 or 3 different levels (depending on the feature).
These levels are organization, project and personal. 
Unlike in Microsoft provided feature's case, if something is turned off on a higher level, that element cannot be turned on for a lower feature level. 
Thus it is not possible to configure "exceptions" for projects or users.

Below is the list of features provided by the extension and what they control.

### Approval Extension

Controls all extension features at the same time. 
Turning it off for the organization is almost equivalent to not having the extension installed.

**Available levels:**
- Organization
- Project

### Approval Tab

Controls whether the [approval tab](/flexible-approvals/tabs/approval-tab.md) should be added to the pipeline runs or not. 
Please note that turning it off makes the own approval hub the only place to cast approval votes.

**Available levels:**
- Organization
- Project

### Approval Hub: Organization

Controls whether the [approval hub](/flexible-approvals/hubs/approval-hub.md) should be present in the organization settings.

**Available levels:**
- Organization

### Approval Hub: Project

Controls whether the [approval hub](/flexible-approvals/hubs/approval-hub.md) should be present in the project settings.

**Available levels:**
- Organization
- Project

### Approval Hub: Own

Controls whether the [approval hub](/flexible-approvals/hubs/approval-hub.md) should be present in the pipelines menu.
Please note that turning it off makes the approval tab the only place to cast approval votes.

**Available levels:**
- Organization
- Project
- Personal

### Approval Widget

Controls whether the [approval widget](/flexible-approvals/widgets/approval-widget.md) should be available to add to dashboards.

**Available levels:**
- Organization
- Project

### Delegate Hub: Organization

Controls whether the [delegate hub](/flexible-approvals/hubs/delegate-hub.md) should be present in the organization settings.

**Available levels:**
- Organization

### Delegate Hub: Project

Controls whether the [delegate hub](/flexible-approvals/hubs/delegate-hub.md) should be present in the project settings.

**Available levels:**
- Organization
- Project

### Delegate Hub: Own

Controls whether the [delegate hub](/flexible-approvals/hubs/delegate-hub.md) should be present in the pipelines menu.

**Available levels:**
- Organization
- Project
- Personal

### Delegate Widget

Controls whether the [delegate widget](/flexible-approvals/widgets/delegate-widget.md) should be available to add to dashboards.

**Available levels:**
- Organization
- Project

## See also

- [Preview features](https://learn.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops)
- [Approval tab](/flexible-approvals/tabs/approval-tab.md)
- [Approval hub](/flexible-approvals/hubs/approval-hub.md)
- [Approval widget](/flexible-approvals/widgets/approval-widget.md)
- [Delegate hub](/flexible-approvals/hubs/delegate-hub.md)
- [Delegate widget](/flexible-approvals/widgets/delegate-widget.md)
- [Glossary](/flexible-approvals/common/gloassary.md)