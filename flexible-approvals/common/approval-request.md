# Approval request

**In this article**
- [Identification](#identification)
- [Approval configuration](#approval-configuration)
- [Approver votes](#approver-votes)
- [See also](#see-also)

List elements of the approval requests' state and describe their effect.

## Identification

The following elements are used to uniquely identify an approval request.

**1. Project**

The project in which the pipeline and thus the approval request is in.

**2. Pipeline**

The pipeline whose run contains the approval request.

**3. Pipeline run**

The pipeline run which contains the approval request.

**4. Approval name**

Name of the approval that was set during the approval request creation.

**5. Stage attempt**

When a pipeline run fails, it is possible to re-run failed jobs. In such cases a new stage attempt is created for that job.
To always be able distinguish  two approval requests, stage attempt is also used next to the previous 4 elements.

![Identification](/flexible-approvals/images/common/approval-request/identification.png)

## Approval configuration

The following elements are all set during the approval request creation and cannot be modified later.
They modify how an approval request behaves, how it can be approved or rejected.

**1. Approvers**

The list of direct approvers. They will be able to cast votes on the approval request unless the other configurations restrict it somehow.

**2. Maximum vote per person**

There are 3 maximum values related to how many votes one person can cast: number of votes, number of direct votes, number of delegated votes.
If number of votes is used, the other two are ignored.
Which means the number of votes define how many direct and delegate votes combined a person can have regardless of their proportion.
In case someone casts a vote after having the maximum number of votes, their oldest vote is replaced with the new vote.

If number of votes is not used, but the number of direct votes is, the person can have at most that amount of direct votes.
In case someone casts a direct vote after having the maximum number of direct votes, their oldest direct vote is replaced with the new vote.
If neither the number of votes, nor the number of direct votes is used, there's no restriction on the number of direct votes.

If number of votes is not used, but the number of delegated votes is, the person can have at most that amount of delegated votes.
In case someone casts a delegated vote after having the maximum number of delegated votes, their oldest delegated vote is replaced with the new vote.
If neither the number of votes, nor the number of delegated votes is used, there's no restriction on the number of delegated votes.

In case none of the maximum numbers is used, there's no restriction on how many votes a person can cast and no votes will be overridden.

**3. Required vote counts**

There are 2 values related to required vote counts: one for approved and one for rejected.

The required approved vote count defines how many approved votes should be cast before an approval request is considered approved.

The required rejected vote count defines how many rejected votes should be cast before an approval request is considered rejected.

Once an approval request is considered approved or rejected, no more votes are allowed to be cast.

**4. Allow own votes**

If own voting is allowed, the person who started the approval request's pipeline run can cast votes if they are approver.
If it is not allowed, the pipeline run's starter cannot cast votes no matter whether they are approver of the approval request or not.

**5. Allow delegates**

If delegates are allowed, the approver list of the approval request consists of its direct approvers and their delegates.
Otherwise, its approver list equals the direct approvers.

![Configuration](/flexible-approvals/images/common/approval-request/configuration.png)
![Configuration - own](/flexible-approvals/images/common/approval-request/configuration-own.png)

## Approver votes

These are the changing elements of the approval request. 
While others are either calculated or set during creation, they can be modified by each vote.

**1. Approver votes**

The list of current approver votes of the approval request.

**2. Approval state**

The current state of the approval request. It can be new, waiting, approved, rejected or cancelled.

An approval request is
- new, if it is created but the waiting/approval process has not been started yet
- waiting, if the waiting/approval process is started, but not completed yet
- approved, if the approval process is completed and the decision is approved
- rejected, if the approval process is completed and the decision is rejected
- cancelled, if it was abandoned in the new or waiting state

![Votes - waiting](/flexible-approvals/images/common/approval-request/votes-waiting.png)
![Votes - approved](/flexible-approvals/images/common/approval-request/votes-approved.png)

## See also

- [CreateApprovalOnAgent@1](/flexible-approvals/tasks/create-approval-on-agent/create-approval-on-agent-v1.md)
- [CreateApprovalOnServer@1](/flexible-approvals/tasks/create-approval-on-server/create-approval-on-server-v1.md)
- [Glossary](/flexible-approvals/common/glossary.md)