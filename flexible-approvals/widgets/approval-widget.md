# Approval widget

**In this article**
- [Usage](#usage)
- [Configuration](#configuration)
- [Disabling](#disabling)
- [See also](#see-also)

Show approval requests through a storable filter.

## Usage

The approval widget can be added to dashboards, then it can be configured to show only the 
approval requests of interest and their relevant details.

![Add widget](/flexible-approvals/images/widgets/approval-widget/add-widget.png)

## Configuration

Once an approval widget was added to a dashboard, it can be configured. 

![Configuration button](/flexible-approvals/images/widgets/approval-widget/configuration-button.png)

The following options are available during configuration:

![Configuration options](/flexible-approvals/images/widgets/approval-widget/configuration-options.png)

**Title**

The title which is present at the top of the widget.

**Size**

Width and height of the widget given in tile count.
Both the width and the height can be set from `2` to `7`.

**Fields**

Fields determine which columns are added to the widget and in which order.
The following fields are available for selection: `Approval`, `Pipeline run`, `Votes`, `Approvers`.

**Order by**

The field based on which the approval requests are ordered and the ordering direction combined.
The following values are available:
- `Approval - ascending`: orders by the approval request name, then stage attemp number ascending
- `Approval - descending`: orders by the approval request name, then stage attemp number descending
- `Pipeline run - ascending`: orders by the pipeline name, then pipeline run number ascending
- `Pipeline run - descending`: orders by the pipeline name, then pipeline run number descending
- `Votes - ascending`: orders by the last vote's time ascending (approval requests without votes become firsts in the list)
- `Votes - descending`: orders by the last vote's time descending (approval requests without votes become lasts in the list)
- `Approvers - ascending`: orders by the approver display names ascending (without changing the list order, shorter lists become firsts)
- `Approvers - descending`: orders by the approver display names descending (without changing the list order, longer lists become firsts)

**Scope**

The scope from which to get the approver requests. 
It serves as a base filter.

Its value can be `Project` or `Organization`. 
In case of `Project`, only the approval requests contained by the current project are considered.
In case of `Organization`, all approval requests are used.

**Filters**

The filters to use for narrowing down the list of in-scope approval requests.
For the available options, please check [Filtering](/flexible-approvals/common/filtering.md#approval-requests).

## Disabling

It is possible to disable the approval widget for the whole organization or for individual projects. 
For the details, please see the [Extension features](/flexible-approvals/common/extension-features.md).

## See also

- [Filtering](/flexible-approvals/common/filtering.md)
- [Extension features](/flexible-approvals/common/extension-features.md)
- [Glossary](/flexible-approvals/common/glossary.md)