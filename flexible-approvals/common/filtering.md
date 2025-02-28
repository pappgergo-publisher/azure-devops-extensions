# Filtering

**In this article**
- [Filter input](#filter-input)
- [Approval requests](#approval-requests)
- [Approver delegations](#approver-delegations)
- [See also](#see-also)

Show how users can filter approval requests and approver delegations.

## Filter input

There are two filter input modes in the extension: form and bar.
The mode only determines how the input can be set, and what values listed automatically.
Outside of that no difference should be between the filter modes, setting the same filter values should result the same list.
That consistency is especially important as the different input modes are for different parts of the extension:
the form input is used in widgets' configuration, while the bar input is available in the hub pages.

Setting multiple filter keys always mean filtering for both, while setting multiple values (if possible) means any of the values should match.
So using *key1* with values *value1* and *value2* and *key2* with *value3* means `(key1 ~ value1 OR key1 ~ value2) AND key2 ~ value3`, 
where `~` symbolizes matching.

## Approval requests

The following filter options are present for approval requests.

**Approval - States**

Input: multiselect list of state names   
Values: `new`, `waiting`, `approved`, `rejected`, `cancelled`

Matches approval requests with any of the selected states.

**Approval - Names**

Input: multiselect list of approval request names   
Values: collection of exisiting approval request names

Matches approval requests with any of the selected approval names.

**Approval - Attempts**

Input: multiselect list of stage attempt numbers   
Values: collection of exisiting approval request stage attempts

Matches approval requests run in any of the selected stage attempts.

**Project**

Input: multiselect list of project names   
Values: collection of exisiting approval request project names

Matches approval requests contained by any of the selected projects.
Not available in the own and project hub pages and in widgets with project scope.

**Pipeline run - Pipelines**

Input: multiselect list of pipeline names   
Values: collection of exisiting approval request pipeline runs

Matches approval requests contained by any of the selected pipelines.

**Pipeline run - Runs**

Input: multiselect list of pipeline run numbers   
Values: collection of exisiting approval request pipeline run numbers

Matches approval requests contained by any of the selected pipeline runs.

**Votes - Voters**

Input: multiselect list of people and groups   
Form values: search from all available people and groups (based on display name and email address)   
Bar values: collection of approvers and voters of existing approval requests

If used without the `decision` filter, matches approval requests having votes with any of the selected people or any member of the selected groups as voter.
If used with the `decision` filter, matches approval requests using the combined filter.

For more details on how the combined filter work, please check Votes - Decisions.

**Votes - Decisions**

Input: multiselect list of decision name   
Values: not voted, approved, rejected

If used without the `voters` filter, matches approval requests with
- no votes received so far (`not voted`)
- at least 1 approved vote (`approved`)
- at least 1 rejected vote (`rejected`)

If used with the `voters` filter, matches approval requests with
- no votes received so far from any of the selected voters (`not voted`)
- at least 1 approved vote from any of the selected voters (`approved`)
- at least 1 rejected vote from any of the selected voters (`rejected`)

**Votes - Last vote (after)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approval requests with their most recent votes casted after the selected time.
Using `now` matches no approval requests, as every vote happened in the past.
Using `never` matches only those approval requests that received no votes so far.

If used with `last vote (before)` filter, and `never` is set as value, the `last vote (before)` is ignored unless it is also set to `never`.

**Votes - Last vote (before)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approval requests with their most recent votes casted before the selected time.
Using `now` matches all approval requests with at least one vote, as every vote happened in the past.
Using `never` matches only those approval requests that received no votes so far.

If used with `last vote (after)` filter, and `never` is set as value, the `last vote (after)` is ignored unless it is also set to `never`.

**Approvers - Approvers**

Input: multiselect list of people and groups   
Form values: search from all available people and groups (based on display name and email address)   
Bar values: collection of approvers and voters of existing approval requests

Matches approval requests with their approver list containing at least one of the selected approvers (after group resolution).

**Approvers - Group resolution**

Input: single select list of group resolution options   
Values: `do no resolve`, `users and groups`, `only users`, `only groups`

Helper filter that does not match anything alone, but changes the behaviour of how `approvers` filter work.
If a group is selected as an approver, it means different users and groups according to different resolution options:
- `do not resolve`: only the selected group, no group members are considered
- `users and groups`: resolve the group memberships and use all direct and indirect members (including the selected group itself)
- `only users`: resolve the group memberships and use all direct and indirect user members
- `only groups`: resolve the group memberships and use all direct and indirect group members (including the selected group itself)

Not selecting a `group resolution` is equivalent of using `do not resolve`.

**Keywords**

Form input: not available   
Bar input: free text   
Values: multiple words

A generic filter that can be used to replace or extend most of the filters above.
It tries to match the words in the filter value against
- approval request name
- stage attempt
- project name
- pipeline name
- pipeline run number
- approval request state
- approver display names

Matches those approval requests in which every word in the filter value is matched to something in the listed attributes.
Please note that the `keywords` filter is case sensitive.

## Approver delegations

**Delegation -  States**

Input: multiselect list of state names   
Values: `inactive`, `active`, `ended`, `cancelled`

Matches approver delegations with any of the selected states. 

**Delegation - Names**

Input: multiselect list of approver delegation names   
Values: collection of exisiting approver delegation names

Matches approver delegations with any of the selected delegation names.

**Timeframe - Start time (after)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approver delegations that start after the selected time.
Using `never` matches no approver delegations as all of them have a start time.

If used with `start time (before)` filter, and `never` is set as value, the `start time (before)` is ignored unless it is also set to `never`.

**Timeframe - Start time (before)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approver delegations that start before the selected time.
Using `never` matches no approver delegations as all of them have a start time.

If used with `start time (after)` filter, and `never` is set as value, the `start time (after)` is ignored unless it is also set to `never`. 

**Timeframe - End time (after)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approver delegations that end after the selected time.
Using `never` matches approver delegations with no predefined end time, i.e. the ones that are active until cancellation.

If used with `end time (before)` filter, and `never` is set as value, the `end time (before)` is ignored unless it is also set to `never`.

**Timeframe - End time (before)**

Input: single select list of time reference values   
Values: `now`, `1 day ago`, `3 days ago`, `7 days ago`, `15 days ago`, `30 days ago`, `60 days ago`, `90 days ago`, `180 days ago`, `365 days ago`, `never`

Matches approver delegations that end before the selected time.
Using `never` matches approver delegations with no predefined end time, i.e. the ones that are active until cancellation.

If used with `end time (after)` filter, and `never` is set as value, the `end time (after)` is ignored unless it is also set to `never`. 

**Timeframe - Scope**

Input: multiselect list of the organization and project names   
Values: collection of scope names of existing approver delegations

Matches approver delegations with any of the selected scopes.
Not available in the in widgets and has the values limited to the organization and the current project in the own and project hub pages.

**Delegators - Delegators**

Input: multiselect list of people and groups   
Form values: search from all available people and groups (based on display name and email address)   
Bar values: collection of delegators and delegates of existing approver delegations

Matches approver delegations having the selected people or any member of the selected groups as delegator.

**Delegates - Delegates**

Input: multiselect list of people and groups   
Form values: search from all available people and groups (based on display name and email address)   
Bar values: collection of delegators and delegates of existing approver delegations

Matches approver delegations with their delegate list containing at least one of the selected delegates (after group resolution).

**Delegates - Group resolution**

Input: single select list of group resolution options   
Values: `do no resolve`, `users and groups`, `only users`, `only groups`

Helper filter that does not match anything alone, but changes the behaviour of how `delegates` filter work.
If a group is selected as a delegate, it means different users and groups according to different resolution options:
- `do not resolve`: only the selected group, no group members are considered
- `users and groups`: resolve the group memberships and use all direct and indirect members (including the selected group itself)
- `only users`: resolve the group memberships and use all direct and indirect user members
- `only groups`: resolve the group memberships and use all direct and indirect group members (including the selected group itself)

Not selecting a `group resolution` is equivalent of using `do not resolve`.

**Keywords**

Form input: not available   
Bar input: free text   
Values: multiple words

A generic filter that can be used to replace or extend most of the filters above.
It tries to match the words in the filter value against
- start time
- end time
- scope
- delegation name
- pipeline run number
- delegator display name
- delegate display names
- delegation state

Matches those approver delegations in which every word in the filter value is matched to something in the listed attributes.
Please note that the `keywords` filter is case sensitive.

## See also

- [Approval request](/flexible-approvals/common/approval-request.md)
- [Approval hub](/flexible-approvals/hubs/approval-hub.md)
- [Approval widget](/flexible-approvals/widgets/approval-widget.md)
- [Approver delegation](/flexible-approvals/common/approver-delegation.md)
- [Delegation hub](/flexible-approvals/hubs/delegation-hub.md)
- [Delegation widget](/flexible-approvals/widgets/delegation-widget.md)
- [Glossary](/flexible-approvals/common/glossary.md)