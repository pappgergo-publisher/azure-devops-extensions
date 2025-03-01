# Glossary

**In this article**
- [Terms](#terms)
- [See also](#see-also)

List of all frequently used words and expressions related to the Flexible Approvals extension.

## Terms

**Approval decision**

The result of the approver votes. The decision can be either approved or rejected.
An approved request means the pipeline run should continue, and a rejected request should fail it.
An approval decision is concluded from the votes when enough approver votes arrived for approval or rejection.

##

**Approval request**

A stopping point introduced into pipeline jobs with one or more approvers.
The approvers can decide whether to approve or reject the approval request and consequently whether the pipeline run's execution should be continued or not.
Technically it means making the tasks providing the stop succeed or fail, 
which can be then ignored by the next tasks and jobs if they are configured so.

For more details on such configurations, see 
[Task control options](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/tasks?view=azure-devops#task-control-options).

##

**Approve**

Casting an approved vote.

##

**Approver**

A person or a group that can cast the vote to approve or reject an approval request.
The approval request's configuration determines who can be its approver.
An approval request can have more than one approver as well.

##

**Approver role**

The approver role describes why a person is considered and approver.

Approver role can be direct approver, member of a direct approver group, 
delegate of a direct approver and member of a delegate group.

##

**Approver vote**

The decision of one person who is either named as approver of part of an approver group.
An approver vote can be either approved or rejected.
When enough approver votes arrive for approval or rejection an approval decision is concluded from them.

##

**Casting vote**

A person named as approver or who is part of an approver group setting their approver vote to either approved or rejected.

##

**Dashboard**

The out-of-the-box Azure DevOps functionality which help presenting information through widgets.

For more details on dashboards, see [Dashboards](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/overview?view=azure-devops).

##

**Delegate**

A person or group that is allowed to cast approver votes in the name of the delegator while the delegation is active.

##

**Delegated approver**

A person or group that is considered as approver due to being a delegate a direct approver or member of a direct approver group.

##

**Delegated vote**

A vote cast by a delegated approver or member of a delegated approver group.

##

**Delegation**

A timeframe set by a person during which the selected delegates can cast approver votes in the name of the person.

##

**Delegator**

A person who has one or more delegates.

##

**Direct approver**

A person or group that is considered as approver due to being directly referenced in the approval request configuration.

##

**Direct vote**

A vote cast by a direct approver or member of a direct approver group.

##

**Feature**

An out-of-the-box Azure DevOps mechanism to allow users turning on and off functionalities and user interface changes.
In this extension it is used to control which capabilities are needed and on which level. 

For more details on features, see [Preview features](https://learn.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops) and
[Extension features](/flexible-approvals/common/extension-features.md).

##

**Hub**

Azure DevOps' term for a page under a so called hub group.
Examples of hub groups are Overview, Boards, Repos, Pipelines, Artifacts, Test Plans, Project settings and Organization settings.

##

**Job**

Execution or organization unit a pipeline. A job contains tasks to execute.

For more details on jobs, see [Specify jobs in your pipeline](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops).

##

**Organization**

Collection of Azure DevOps projects, sometimes referred as project collection as well in Azure DevOps and its documentation pages.
For more details on organizations, see 
[Organization management overview](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/organization-management?view=azure-devops).

##

**Project**

A project in Azure DevOps is a place for users to plan, track progress, and collaborate on building software solutions. 
A project represents a fundamental container where you can store data and source code.

For more details on projects, see [About projects](https://learn.microsoft.com/en-us/azure/devops/organizations/projects/about-projects?view=azure-devops).

##

**Pipeline**

Pipelines are the parts of Azure DevOps that automatically build, test, and deploy code projects.
Even though there are more pipeline types, in the extension's context the term is only used to refer to the yaml (build) pipelines.

For more details on pipelines, see 
[What is Azure Pipelines?](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops).

##

**Pipeline run**

A pipeline represents one execution of a pipeline.

For more details on pipeline runs, see [Pipeline runs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/runs?view=azure-devops).

##

**Reject**

Casting a rejected vote.

##

**Stage**

Organization unit a pipeline, a logical boundary in pipelines. A stage contains jobs.

For more details on stages, see [Add stages, dependencies, & conditions](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/stages?view=azure-devops).

##

**Tab**

A tab is part of pipeline run's user interface which allows switching the content to show about the pipeline run.

##

**Task**

A task performs an action in a pipeline. The extension provides tasks to create approval requests and wait for the approval decision.

For more details on tasks, see [Azure Pipelines task reference](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/?view=azure-pipelines).

##

**Voter**

An approver who has already casted their vote on an approval request is considered as a voter of the said request.

##

**Widget**

A widgets is a tool to smartly format data and make them easily consumable. Widgets are placed into dashboards.

For more details on widgets, see [Add widgets to a dashboard](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/add-widget-to-dashboard).

## See also

- [About projects](https://learn.microsoft.com/en-us/azure/devops/organizations/projects/about-projects?view=azure-devops)
- [Add stages, dependencies, & conditions](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/stages?view=azure-devops)
- [Add widgets to a dashboard](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/add-widget-to-dashboard)
- [Azure Pipelines task reference](https://learn.microsoft.com/en-us/azure/devops/pipelines/tasks/reference/?view=azure-pipelines)
- [Dashboards](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/overview?view=azure-devops)
- [Organization management overview](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/organization-management?view=azure-devops)
- [Pipeline runs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/runs?view=azure-devops)
- [Preview features](https://learn.microsoft.com/en-us/azure/devops/project/navigation/preview-features?view=azure-devops)
- [Specify jobs in your pipeline](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops)
- [Task control options](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/tasks?view=azure-devops#task-control-options)
- [What is Azure Pipelines?](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/what-is-azure-pipelines?view=azure-devops)
- [Extension features](/flexible-approvals/common/extension-features.md)