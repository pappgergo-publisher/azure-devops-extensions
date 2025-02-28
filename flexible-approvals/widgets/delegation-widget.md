# Delegation widget

**In this article**
- [Usage](#usage)
- [Configuration](#configuration)
- [Disabling](#disabling)
- [See also](#see-also)

Show approver delegations through a storable filter.

## Usage

The delegation widget can be added to dashboards, then it can be configured to show only the 
approver delegations of interest and their relevant details.

![Add widget](/flexible-approvals/images/widgets/delegation-widget/add-widget.png)

## Configuration

Once an delegation widget was added to a dashboard, it can be configured. 

![Configuration button](/flexible-approvals/images/widgets/delegation-widget/configuration-button.png)

The following options are available during configuration:

![Configuration options](/flexible-approvals/images/widgets/delegation-widget/configuration-options.png)

**Title**

The title which is present at the top of the widget.

**Size**

Width and height of the widget given in tile count.
Both the width and the height can be set from `2` to `7`.

**Fields**

Fields determine which columns are added to the widget and in which order.
The following fields are available for selection: `Delegation`, `Timeframe`, `Delegators`, `Delegates`.

**Order by**

The field based on which the approver delegations are ordered and the ordering direction combined.
The following values are available:
- `Delegation - ascending`: orders by the delegation name ascending
- `Delegation - descending`: orders by the delegation name descending
- `Timeframe - ascending`: orders by start time, then end time ascending
- `Timeframe - descending`: orders by start time, then end time descending
- `Delegators - ascending`: orders by the delegator display name ascending
- `Delegators - descending`: orders by the delegator display name descending
- `Delegates - ascending`: orders by the delegate display names ascending (without changing the list order, shorter lists become firsts)
- `Delegates - descending`: orders by the delegate display names ascending (without changing the list order, longer lists become firsts)

**Scope**

The scope from which to get the approver delegations. 
It serves as a base filter.

Its value can be `Project` or `Organization`. 
In case of `Project`, only the approver delegations with organization scope and scope matching the current project are considered.
In case of `Organization`, all approver delegations are used.

**Filters**

The filters to use for narrowing down the list of in-scope approver delegations.
For the available options, please check [Filtering](/flexible-approvals/common/filtering.md#approver-delegations).

## Disabling

It is possible to disable the delegation widget for the whole organization or for individual projects. 
For the details, please see the [Extension features](/flexible-approvals/common/extension-features.md).

## See also

- [Filtering](/flexible-approvals/common/filtering.md)
- [Extension features](/flexible-approvals/common/extension-features.md)
- [Glossary](/flexible-approvals/common/glossary.md)