# CreateApprovalOnServer@1 - Create approval (server) v1 task

**In this article**
- [Syntax](#syntax)
- [Inputs](#inputs)
- [Output variables](#output-variables)
- [Remarks](#remarks)
- [Examples](#examples)
- [Requirements](#requirements)
- [See also](#see-also)

Create an approval request without waiting for its result.

## Syntax

```yaml
- task: CreateApprovalOnServer@1
  inputs:
    organizationName: # string. Required. 
    approvalName: # string. Required. 
    approverList: # string. Aliases: approvers, approver. Required.
    #approverListDelimiter: # string. Aliases: approverDelimiter, delimiter. Optional. Use when multiple approvers are added and approverList is in one line.
    #requiredApprovedVoteCount: 1 # number. Optional. Default: 1.
    #requiredRejectedVoteCount: 1 # number. Optional. Default: 1.
    #allowOwnVote: false # boolean. Optional. Default: false.
    #retainRun: true # boolean. Optional. Default: true.
    #retainRunForDays: 365000 # number. Optional. Use when retainRun = true. Default: 365000.
    #maximumVotePerPerson: 1 # number. Optional. Default: 1.
    #maximumDirectVotePerPerson: 0 # number. Optional. Use when maximumVotePerPerson = 0. Default: 0.
    #maximumDelegateVotePerPerson: 0 # number. Optional. Use when maximumVotePerPerson = 0. Default: 0.
    #allowDelegates: true # boolean. Optional. Default: true.
```

## Inputs

**`organizationName` - Organization name**  
`string`. Required.

Name of the Azure DevOps organization the created approval request belongs to. 
If your Azure DevOps organization URL is https://dev.azure.com/example/, then the expected value is `example`.

**`approvalName` - Approval name**  
`string`. Required.

Name of the created approval request. It must be unique within a pipeline run.

**`approverList` - Approver list**  
Input aliases: `approvers`, `approver`. `string`. Required.

Display name or email address of the people and/or groups whose members count as direct approvers and can approve/reject the created approval request. 
It can be a list when one approver per line is provided. Or the approvers can be in one line, in that case `Approver list delimiter` needs to be set.

Please note that due to technical limitations, this task can handle 10 approvers at most. In case more than 10 is provided,
only the first 10 is used and the rest is ignored.

If a group is set as an approver, it must either be an organization level group or come from the same project as the approval request.
This restriction reduces the opportunity for a name collision. However, if in any case, more than one identity matches the approver name/email,
always the first one found will be used.

**`approverListDelimiter` - Approver list delimiter**  
Input aliases: `approverDelimiter`, `delimiter`. `string`. Optional.

The delimiter to use to separate approvers when the `Approver list` is given in one line.

**`requiredApprovedVoteCount` - Required approved vote count**  
`number`. Optional. Default value: `1`.

The number of approved votes required to consider the created approval request approved.

**`requiredRejectedVoteCount` - Required rejected vote count**  
`number`. Optional. Default value: `1`.

The number of rejected votes required to consider the created approval request rejected.

**`allowOwnVote` - Allow own vote?**  
`boolean`. Optional. Default value: `false`.

If set to `true`, the person starting the pipeline run, which contains the created approval request, can also approve/reject it.

**`retainRun` - Retain run?**  
`boolean`. Optional. Default value: `true`.

If set to `true`, a retention lease will be created for the pipeline run containing the created approval request. 
The pipeline run will be retained for the number of days provided in `Retain run for days`.

**`retainRunForDays` - Retain run for days**  
`number`. Optional. Use when `retainRun = true`. Default value: `365000`.

The number of days the pipeline run containing the created approval request should be retained.

**`maximumVotePerPerson` - Maximum vote per person**  
`number`. Optional. Default value: `1`.

The number of votes one person can provide. If someone approves or rejects the approval request after having the maximum number of votes, 
the oldest vote will be replaced by the new vote. This behaviour can be turned off by setting the value to `0`.

**`maximumDirectVotePerPerson` - Maximum vote per person as direct approver**  
`number`. Optional. Use when `Maximum vote per person = 0`. Default value: `0`.

The number of direct votes one person can provide. If someone approves or rejects the approval request as direct approver after having the maximum number of direct votes, 
the oldest direct vote will be replaced by the new vote. This behaviour can be turned off by setting the value to `0`.

**`maximumDelegateVotePerPerson` - Maximum vote per person as delegated approver**  
`number`. Optional. Use when `Maximum vote per person = 0`. Default value: `0`.

The number of delegated votes one person can provide. If someone approves or rejects the approval request as delegate after having the maximum number of delegate votes, 
the oldest delegate vote will be replaced by the new vote. This behaviour can be turned off by setting the value to `0`.

**`allowDelegates` - Allow delegates?**  
`boolean`. Optional. Default value: `false`.

If set to `true`, the delegates of the direct approvers can also approve/reject the created approval request.

### Task control options

All tasks have control options in addition to their task inputs. 
For more information, see [Control options and common task properties](https://learn.microsoft.com/en-us/azure/devops/pipelines/yaml-schema/steps-task?view=azure-pipelines#common-task-properties).

## Output variables

None.

## Remarks

Use this task to create an approval request. It does not interrupt the execution of the pipeline runs, 
but its separation from the WaitForApprovalOnServer task is mostly due to technical reasons. 
Thus even though it is possible to postpone the execution of a waiting task, it is advised to put them as close to each other as possible.

Please note that this task can be used instead of CreateApprovalOnAgent as the created approval request only depends on the
input parameters, not the type of task used for the creation.

## Examples

**Static approver**  
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

**Static approver list**  
```yaml
steps:
- task: CreateApprovalOnServer@1
  displayName: Create approval
  inputs:
    organizationName: example-org
    approvalName: server-approval
    approvers: |
      Example Approver
      approver@example.com
      Example Group
- task: WaitForApprovalOnServer@1
  displayName: Wait for approval
  inputs:
    organizationName: example-org  
    approvalName: server-approval
```

**Dynamic approver list**
```yaml
parameters:
- name: approvers
  displayName: Approvers
  type: object
  default: 
  - Example Approver
  - approver@example.com
  - Example Group

steps:
- task: CreateApprovalOnServer@1
  displayName: Create approval
  inputs:
    organizationName: example-org
    approvalName: server-approval
    approvers: ${{ join(';', parameters.approvers) }}
    delimiter: ';'
- task: WaitForApprovalOnServer@1
  displayName: Wait for approval
  inputs:
    organizationName: example-org  
    approvalName: server-approval
```

**Complex configuration**
```yaml
parameters:
- name: approver
  displayName: Approver
  type: string
  values: 
  - Example Group 1
  - Example Group 2

steps:
- task: CreateApprovalOnServer@1
  displayName: Create approval
  inputs:
    organizationName: example-org
    approvalName: server-approval
    approver: ${{ parameters.approver }}
    retainRun: true
    retainRunForDays: 365 # Retain run for a year
    allowOwnVote: true
    requiredApprovedVoteCount: 2 # Require two approved,
    requiredRejectedVoteCount: 2 # or two rejected votes to complete the request
    allowDelegates: true
    maximumVotePerPerson: 0 # Turn off maximum vote per person,
    maximumDirectVotePerPerson: 1 # and allow 1 direct
    maximumDelegateVotePerPerson: 1 # plus 1 delegated vote per person
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
- [WaitForApprovalOnAgent@1](/flexible-approvals/tasks/wait-for-approval-on-agent/wait-for-approval-on-agent-v1.md)
- [WaitForApprovalOnServer@1](/flexible-approvals/tasks/wait-for-approval-on-server/wait-for-approval-on-server-v1.md)
- [Glossary](/flexible-approvals/common/glossary.md)
- [Approval request](/flexible-approvals/common/approval-request.md)