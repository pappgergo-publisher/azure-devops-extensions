# Approver delegation

**In this article**
- [Identification](#identification)
- [Delegate configuration](#delegate-configuration)
- [Delegation timeframe](#delegation-timeframe)
- [See also](#see-also)

List elements of the approver delegations' state and describe their effect.

## Identification

The following elements are used to uniquely identify an approver delegation.

**1. Delegator**

The person who creates the delegation and becomes the delegator.

**2. Create time**

The time of the approver delegation's creation in milliseconds.

![Identification](/flexible-approvals/images/common/approver-delegation/identification.md)

## Delegate configuration

The following elements are all set during the approver delegation creation and cannot be modified later.
They determine how a delegation is named and who is considered a delegate of the delegator.

**1. Delegation name**

A name that the delegator sets. Its only purpose is to help identify the delegation for the users.
Thus it does not have to be unique, but using unique values are encouraged.

**2. Delegates**

The list of delegates for the delegator. A delegate can be a person or a group as well.

**3. Scope**

The scope in which the delegates will become able to cast votes instead of the delegator.
It can either be the whole organization or the project in which the delegation is created.

![Delegate configuration](/flexible-approvals/images/common/approver-delegation/delegate-configuration.md)

## Delegation timeframe

These elements determine when the delegation is considered active and when the delegates can cast votes in the name of the delegator.

**1. Start time**

The time in milliseconds from when the delegation counts as active.
Every approver delegation must have a start time.

**2. End time**

The time in milliseconds after when the delegation counts as ended.
If end time is not provided, the delegation won't end unless it is cancelled.
When a delegation is cancelled, the time of the cancellation is used instead of the originally set end time.

**3. Delegation state**

The current state of the approver delegation. It can be inactive, active, ended or cancelled.

An approver delegation is
- inactive, if it is not cancelled and the current time is before its start time
- active, if it is not cancelled and the current time is between its start and end times
- ended, if it is not cancelled and the current time is after its end time
- cancelled, if the the cancel action was used on it

![Delegation timeframe](/flexible-approvals/images/common/approver-delegation/delegation-timeframe.md)

## See also

- [Delegation hub](/flexible-approvals/hubs/delegation-hub.md)
- [Glossary](/flexible-approvals/common/glossary.md)