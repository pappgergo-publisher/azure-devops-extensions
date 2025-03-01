# WaitForApprovalOnServer@1 - Wait for approval (server) v1 task

**In this article**
- [Syntax](#syntax)
- [Inputs](#inputs)
- [Output variables](#output-variables)
- [Remarks](#remarks)
- [Examples](#examples)
- [Requirements](#requirements)
- [See also](#see-also)

Wait for an already created, new approval request.

## Syntax

```yaml
- task: WaitForApprovalOnServer@1
  inputs:
    organizationName: # string. Required.
    approvalName: # string. Required.
```

## Inputs

**`organizationName` - Organization name**  
`string`. Required.

Name of the Azure DevOps organization the approval request belongs to. 
If your Azure DevOps organization URL is https://dev.azure.com/example/, then the expected value is `example`.

**`approvalName` - Approval name**  
`string`. Required.

Name of the approval request to wait for.

### Task control options

All tasks have control options in addition to their task inputs. 
For more information, see [Control options and common task properties](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/steps-task?view=azure-pipelines#common-task-properties).

## Output variables

None.

## Remarks

Use this task to wait for an approval request to be approved or rejected. The approval request must be in the new state to be a valid input for this task.

It is possible to combine this task with both CreateApprovalOnAgent and CreateApprovalOnServer as the created approval request only depends on the
input parameters, not the type of task used for the creation.

Please consider configuring timeouts for both the WaitForApprovalOnServer task and its job, to avoid cancellation of your approval request.
For more information, see [Server jobs](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops#server-jobs).


## Examples

```yaml
steps:
- task: CreateApprovalOnServer@1
  displayName: Create approval
  inputs:
    organizationName: example-org
    approvalName: server-approval
    approver: Example Approver
- task: WaitForApprovalOnServer@1
  displayName: Wait for approval
  inputs:
    organizationName: example-org  
    approvalName: server-approval
```

## Requirements

|Requirement|Description|
|---|---|
|Pipeline types|YAML|
|Runs on|Server|
|[Demands](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/pool-demands?view=azure-pipelines)|None|
|[Capabilities](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/agents?view=azure-devops#capabilities)|This task does not satisfy any demands for subsequent tasks in the job|
|[Command restrictions](https://learn.microsoft.com/en-us/azure/devops/pipelines/security/templates?view=azure-devops#agent-logging-command-restrictions)|Any|
|[Settable variables](https://learn.microsoft.com/en-us/azure/devops/pipelines/security/templates?view=azure-devops#agent-logging-command-restrictions)|Any|
|Agent version|All supported agent versions|
|Task category|Deploy|

## See also
- [CreateApprovalOnAgent@1](/flexible-approvals/tasks/create-approval-on-agent/create-approval-on-agent-v1.md)
- [CreateApprovalOnServer@1](/flexible-approvals/tasks/create-approval-on-server/create-approval-on-server-v1.md)
- [WaitForApprovalOnAgent@1](/flexible-approvals/tasks/wait-for-approval-on-agent/wait-for-approval-on-agent-v1.md)
- [Glossary](/flexible-approvals/common/glossary.md)