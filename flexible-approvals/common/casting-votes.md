# Casting votes

**In this article**
- [Requirements](#requirements)
- [Steps](#steps)
- [Result](#result)
- [See also](#see-also)

Show how approvers can cast votes on approval requests.

## Requirements

In order to be able to cast votes all of the following conditions must be met:
- the approval request must be in waiting state
- the person casting the vote must be
  - a direct approver, or
  - member of a direct approver group, or
  - delegate of a direct approver ( if delegated votes are allowed), or
  - delegate of a direct approver group's member (if delegated votes are allowed), or
  - member of a delegate group (if delegated votes are allowed)
- the person casting the vote must be different from the one who started the approval request's pipeline run, or own votes must be allowed

## Steps

1. Open the [approval tab](/flexible-approvals/tabs/approval-tab.md) or the own [approval hub](/flexible-approvals/hubs/approval-hub.md).
2. To cast an approved vote, use the Approve or Approve all button.    To cast a rejected vote, use the Reject or Reject all button.

   ![Step 2](/flexible-approvals/images/common/casting-votes/step2.png)

3. Select in which approver role want to cast the vote. 
   Might be important in case there are restrictions on how much direct or delegated votes a person can cast.

   ![Step 3](/flexible-approvals/images/common/casting-votes/step3.png)

4. Optionally add a comment describing your the reason for the decision.
5. Click on the Yes button.

   ![Step 4-5](/flexible-approvals/images/common/casting-votes/step4-5.png)

## Result

If
- Approve is used, an approved vote is added to the approval request
- Approve all is used, an approved vote is added to all approval request for which the selected role is applicable
- Reject is used, a rejected vote is added to the approval request
- Reject all is used, a rejected vote is added to all approval request for which the selected role is applicable

If due to the added vote, any of the approver vote count thresholds (all count / direct vote count / delegated vote count) would be exceeded,
the new vote replaces the approver's oldest matching vote (any vote / direct vote / delegated vote).

If after adding the vote either the approved or rejected votes' count reaches the configured limit,
the approval request's state is changed from waiting to approve or rejected.

## See also

- [Approval tab](/flexible-approvals/tabs/approval-tab.md)
- [Approval hub](/flexible-approvals/hubs/approval-hub.md)
- [Approval request](/flexible-approvals/common/approval-request.md)
- [Glossary](/flexible-approvals/common/glossary.md)