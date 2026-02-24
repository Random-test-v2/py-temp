# Subscriptions

## Overview

### Available Operations

* [create_subscription](#create_subscription) - Create subscription
* [add_subscription_addon](#add_subscription_addon) - Add addon to subscription
* [remove_subscription_addon](#remove_subscription_addon) - Remove addon from subscription
* [update_subscription_line_item](#update_subscription_line_item) - Update subscription line item
* [delete_subscription_line_item](#delete_subscription_line_item) - Delete subscription line item
* [query_subscription](#query_subscription) - Query subscriptions
* [get_subscription_usage](#get_subscription_usage) - Get usage by subscription
* [get_subscription](#get_subscription) - Get subscription
* [update_subscription](#update_subscription) - Update subscription
* [activate_subscription](#activate_subscription) - Activate draft subscription
* [get_subscription_addon_associations](#get_subscription_addon_associations) - Get active addon associations
* [cancel_subscription](#cancel_subscription) - Cancel subscription
* [execute_subscription_change](#execute_subscription_change) - Execute subscription plan change
* [preview_subscription_change](#preview_subscription_change) - Preview subscription plan change
* [get_subscription_entitlements](#get_subscription_entitlements) - Get subscription entitlements
* [get_subscription_upcoming_grants](#get_subscription_upcoming_grants) - Get upcoming credit grant applications
* [create_subscription_line_item](#create_subscription_line_item) - Create subscription line item
* [pause_subscription](#pause_subscription) - Pause a subscription
* [list_subscription_pauses](#list_subscription_pauses) - List all pauses for a subscription
* [resume_subscription](#resume_subscription) - Resume a paused subscription
* [get_subscription_v2](#get_subscription_v2) - Get subscription (V2)
* [list_all_subscription_schedules](#list_all_subscription_schedules) - List all subscription schedules
* [get_subscription_schedule](#get_subscription_schedule) - Get subscription schedule
* [cancel_subscription_schedule](#cancel_subscription_schedule) - Cancel subscription schedule
* [list_subscription_schedules](#list_subscription_schedules) - List subscription schedules

## create_subscription

Use when onboarding a customer to a plan or starting a new subscription. Ideal for draft subscriptions (activate later) or active from start.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSubscription" method="post" path="/subscriptions" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.create_subscription(billing_cadence="ONETIME", billing_period="DAILY", currency="New Leu", plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                         | Type                                                                                                                                              | Required                                                                                                                                          | Description                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `billing_cadence`                                                                                                                                 | [models.TypesBillingCadence](../../models/typesbillingcadence.md)                                                                                 | :heavy_check_mark:                                                                                                                                | N/A                                                                                                                                               |
| `billing_period`                                                                                                                                  | [models.TypesBillingPeriod](../../models/typesbillingperiod.md)                                                                                   | :heavy_check_mark:                                                                                                                                | N/A                                                                                                                                               |
| `currency`                                                                                                                                        | *str*                                                                                                                                             | :heavy_check_mark:                                                                                                                                | N/A                                                                                                                                               |
| `plan_id`                                                                                                                                         | *str*                                                                                                                                             | :heavy_check_mark:                                                                                                                                | N/A                                                                                                                                               |
| `addons`                                                                                                                                          | List[[models.DtoAddAddonToSubscriptionRequest](../../models/dtoaddaddontosubscriptionrequest.md)]                                                 | :heavy_minus_sign:                                                                                                                                | Addons represents addons to be added to the subscription during creation                                                                          |
| `billing_cycle`                                                                                                                                   | [Optional[models.TypesBillingCycle]](../../models/typesbillingcycle.md)                                                                           | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `billing_period_count`                                                                                                                            | *Optional[int]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `collection_method`                                                                                                                               | [Optional[models.TypesCollectionMethod]](../../models/typescollectionmethod.md)                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `commitment_amount`                                                                                                                               | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | CommitmentAmount is the minimum amount a customer commits to paying for a billing period                                                          |
| `commitment_duration`                                                                                                                             | [Optional[models.TypesBillingPeriod]](../../models/typesbillingperiod.md)                                                                         | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `coupons`                                                                                                                                         | List[*str*]                                                                                                                                       | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `credit_grants`                                                                                                                                   | List[[models.DtoCreateCreditGrantRequest](../../models/dtocreatecreditgrantrequest.md)]                                                           | :heavy_minus_sign:                                                                                                                                | Credit grants to be applied when subscription is created                                                                                          |
| `customer_id`                                                                                                                                     | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | customer_id is the flexprice customer id<br/>and it is prioritized over external_customer_id in case both are provided.                           |
| `customer_timezone`                                                                                                                               | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | Timezone of the customer.<br/>If not set, the default value is UTC.                                                                               |
| `enable_true_up`                                                                                                                                  | *Optional[bool]*                                                                                                                                  | :heavy_minus_sign:                                                                                                                                | Enable Commitment True Up Fee                                                                                                                     |
| `end_date`                                                                                                                                        | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `external_customer_id`                                                                                                                            | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | external_customer_id is the customer id in your DB<br/>and must be same as what you provided as external_id while creating the customer in flexprice. |
| `gateway_payment_method_id`                                                                                                                       | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `invoice_billing`                                                                                                                                 | [Optional[models.TypesInvoiceBilling]](../../models/typesinvoicebilling.md)                                                                       | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `line_item_commitments`                                                                                                                           | Dict[str, [models.DtoLineItemCommitmentConfig](../../models/dtolineitemcommitmentconfig.md)]                                                      | :heavy_minus_sign:                                                                                                                                | LineItemCommitments allows setting commitment configuration per line item (keyed by price_id)                                                     |
| `line_item_coupons`                                                                                                                               | Dict[str, List[*str*]]                                                                                                                            | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `line_items`                                                                                                                                      | List[[models.DtoCreateSubscriptionLineItemRequest](../../models/dtocreatesubscriptionlineitemrequest.md)]                                         | :heavy_minus_sign:                                                                                                                                | LineItems are extra line items to add at creation (each with price_id or price), in addition to plan prices                                       |
| `lookup_key`                                                                                                                                      | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `metadata`                                                                                                                                        | Dict[str, *str*]                                                                                                                                  | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `overage_factor`                                                                                                                                  | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | OverageFactor is a multiplier applied to usage beyond the commitment amount                                                                       |
| `override_entitlements`                                                                                                                           | List[[models.DtoOverrideEntitlementRequest](../../models/dtooverrideentitlementrequest.md)]                                                       | :heavy_minus_sign:                                                                                                                                | OverrideEntitlements allows customizing specific entitlements for this subscription                                                               |
| `override_line_items`                                                                                                                             | List[[models.DtoOverrideLineItemRequest](../../models/dtooverridelineitemrequest.md)]                                                             | :heavy_minus_sign:                                                                                                                                | OverrideLineItems allows customizing specific prices for this subscription                                                                        |
| `parent_subscription_id`                                                                                                                          | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | ParentSubscriptionID is the parent subscription ID for hierarchy (e.g. child subscription under a parent)                                         |
| `payment_behavior`                                                                                                                                | [Optional[models.TypesPaymentBehavior]](../../models/typespaymentbehavior.md)                                                                     | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `payment_terms`                                                                                                                                   | [Optional[models.TypesPaymentTerms]](../../models/typespaymentterms.md)                                                                           | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `phases`                                                                                                                                          | List[[models.DtoSubscriptionPhaseCreateRequest](../../models/dtosubscriptionphasecreaterequest.md)]                                               | :heavy_minus_sign:                                                                                                                                | Phases represents subscription phases to be created with the subscription                                                                         |
| `proration_behavior`                                                                                                                              | [Optional[models.TypesProrationBehavior]](../../models/typesprorationbehavior.md)                                                                 | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `start_date`                                                                                                                                      | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `subscription_status`                                                                                                                             | [Optional[models.TypesSubscriptionStatus]](../../models/typessubscriptionstatus.md)                                                               | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `tax_rate_overrides`                                                                                                                              | List[[models.DtoTaxRateOverride](../../models/dtotaxrateoverride.md)]                                                                             | :heavy_minus_sign:                                                                                                                                | tax_rate_overrides is the tax rate overrides	to be applied to the subscription                                                                    |
| `trial_end`                                                                                                                                       | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `trial_start`                                                                                                                                     | *Optional[str]*                                                                                                                                   | :heavy_minus_sign:                                                                                                                                | N/A                                                                                                                                               |
| `retries`                                                                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                  | :heavy_minus_sign:                                                                                                                                | Configuration to override the default retry behavior of the client.                                                                               |

### Response

**[models.DtoSubscriptionResponse](../../models/dtosubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## add_subscription_addon

Use when adding an optional product or add-on to an existing subscription (e.g. extra storage or support tier).

### Example Usage

<!-- UsageSnippet language="python" operationID="addSubscriptionAddon" method="post" path="/subscriptions/addon" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.add_subscription_addon(addon_id="<id>", subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `addon_id`                                                                                          | *str*                                                                                               | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `subscription_id`                                                                                   | *str*                                                                                               | :heavy_check_mark:                                                                                  | N/A                                                                                                 |
| `line_item_commitments`                                                                             | Dict[str, [models.DtoLineItemCommitmentConfig](../../models/dtolineitemcommitmentconfig.md)]        | :heavy_minus_sign:                                                                                  | LineItemCommitments allows setting commitment configuration per addon line item (keyed by price_id) |
| `metadata`                                                                                          | Dict[str, *Any*]                                                                                    | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `start_date`                                                                                        | *Optional[str]*                                                                                     | :heavy_minus_sign:                                                                                  | N/A                                                                                                 |
| `retries`                                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                    | :heavy_minus_sign:                                                                                  | Configuration to override the default retry behavior of the client.                                 |

### Response

**[models.DtoAddonAssociationResponse](../../models/dtoaddonassociationresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## remove_subscription_addon

Use when removing an add-on from a subscription (e.g. downgrade or opt-out).

### Example Usage

<!-- UsageSnippet language="python" operationID="removeSubscriptionAddon" method="delete" path="/subscriptions/addon" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.remove_subscription_addon(addon_association_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `addon_association_id`                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `reason`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_subscription_line_item

Use when changing a subscription line item (e.g. quantity or price). Implemented by ending the current line and creating a new one for clean billing.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSubscriptionLineItem" method="put" path="/subscriptions/lineitems/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.update_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `id`                                                                              | *str*                                                                             | :heavy_check_mark:                                                                | Line Item ID                                                                      |
| `amount`                                                                          | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | Amount is the new price amount that overrides the original price                  |
| `billing_model`                                                                   | [Optional[models.TypesBillingModel]](../../models/typesbillingmodel.md)           | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_amount`                                                               | *Optional[float]*                                                                 | :heavy_minus_sign:                                                                | Commitment fields                                                                 |
| `commitment_duration`                                                             | [Optional[models.TypesBillingPeriod]](../../models/typesbillingperiod.md)         | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_overage_factor`                                                       | *Optional[float]*                                                                 | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_quantity`                                                             | *Optional[float]*                                                                 | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_true_up_enabled`                                                      | *Optional[bool]*                                                                  | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_type`                                                                 | [Optional[models.TypesCommitmentType]](../../models/typescommitmenttype.md)       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `commitment_windowed`                                                             | *Optional[bool]*                                                                  | :heavy_minus_sign:                                                                | N/A                                                                               |
| `effective_from`                                                                  | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | EffectiveFrom for the existing line item (if not provided, defaults to now)       |
| `metadata`                                                                        | Dict[str, *str*]                                                                  | :heavy_minus_sign:                                                                | Metadata for the new line item                                                    |
| `tier_mode`                                                                       | [Optional[models.TypesBillingTier]](../../models/typesbillingtier.md)             | :heavy_minus_sign:                                                                | N/A                                                                               |
| `tiers`                                                                           | List[[models.DtoCreatePriceTier](../../models/dtocreatepricetier.md)]             | :heavy_minus_sign:                                                                | Tiers determines the pricing tiers for this line item                             |
| `transform_quantity`                                                              | [Optional[models.PriceTransformQuantity]](../../models/pricetransformquantity.md) | :heavy_minus_sign:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.DtoSubscriptionLineItemResponse](../../models/dtosubscriptionlineitemresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_subscription_line_item

Use when removing a charge or seat from a subscription (e.g. downgrade). Line item ends; retained for history but no longer billed.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteSubscriptionLineItem" method="delete" path="/subscriptions/lineitems/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.delete_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Line Item ID                                                        |
| `effective_from`                                                    | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSubscriptionLineItemResponse](../../models/dtosubscriptionlineitemresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_subscription

Use when listing or searching subscriptions (e.g. admin view or customer subscription list). Returns a paginated list; supports filtering by customer, plan, status.

### Example Usage

<!-- UsageSnippet language="python" operationID="querySubscription" method="post" path="/subscriptions/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.query_subscription()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `active_at`                                                                                   | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | ActiveAt filters subscriptions that are active at the given time                              |
| `billing_cadence`                                                                             | List[[models.TypesBillingCadence](../../models/typesbillingcadence.md)]                       | :heavy_minus_sign:                                                                            | BillingCadence filters by billing cadence                                                     |
| `billing_period`                                                                              | List[[models.TypesBillingPeriod](../../models/typesbillingperiod.md)]                         | :heavy_minus_sign:                                                                            | BillingPeriod filters by billing period                                                       |
| `customer_id`                                                                                 | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | CustomerID filters by customer ID                                                             |
| `end_time`                                                                                    | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `expand`                                                                                      | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `external_customer_id`                                                                        | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | ExternalCustomerID filters by external customer ID                                            |
| `filters`                                                                                     | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]                     | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `invoicing_customer_ids`                                                                      | List[*str*]                                                                                   | :heavy_minus_sign:                                                                            | InvoicingCustomerIDs filters by invoicing customer ID                                         |
| `limit`                                                                                       | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `offset`                                                                                      | *Optional[int]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `order`                                                                                       | [Optional[models.TypesSubscriptionFilterOrder]](../../models/typessubscriptionfilterorder.md) | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `parent_subscription_ids`                                                                     | List[*str*]                                                                                   | :heavy_minus_sign:                                                                            | ParentSubscriptionIDs filters by parent subscription IDs                                      |
| `plan_id`                                                                                     | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | PlanID filters by plan ID                                                                     |
| `sort`                                                                                        | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                         | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `start_time`                                                                                  | *Optional[str]*                                                                               | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `status`                                                                                      | [Optional[models.TypesStatus]](../../models/typesstatus.md)                                   | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `subscription_ids`                                                                            | List[*str*]                                                                                   | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `subscription_status`                                                                         | List[[models.TypesSubscriptionStatus](../../models/typessubscriptionstatus.md)]               | :heavy_minus_sign:                                                                            | SubscriptionStatus filters by subscription status                                             |
| `with_line_items`                                                                             | *Optional[bool]*                                                                              | :heavy_minus_sign:                                                                            | WithLineItems includes line items in the response                                             |
| `retries`                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                              | :heavy_minus_sign:                                                                            | Configuration to override the default retry behavior of the client.                           |

### Response

**[models.DtoListSubscriptionsResponse](../../models/dtolistsubscriptionsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription_usage

Use when showing usage for a subscription (e.g. in a portal or for overage checks). Supports time range and filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionUsage" method="post" path="/subscriptions/usage" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_usage(subscription_id="123", end_time="2024-03-20T00:00:00Z", lifetime_usage=False, start_time="2024-03-13T00:00:00Z")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `subscription_id`                                                   | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 | 123                                                                 |
| `end_time`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 2024-03-20T00:00:00Z                                                |
| `lifetime_usage`                                                    | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 | false                                                               |
| `start_time`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 | 2024-03-13T00:00:00Z                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DtoGetUsageBySubscriptionResponse](../../models/dtogetusagebysubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription

Use when you need to load a single subscription (e.g. for a billing portal or to check status).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscription" method="get" path="/subscriptions/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSubscriptionResponse](../../models/dtosubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_subscription

Use when changing subscription details (e.g. quantity, billing anchor, or parent). Supports partial update; send "" to clear parent_subscription_id.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateSubscription" method="put" path="/subscriptions/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.update_subscription(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                    | *str*                                                                                                   | :heavy_check_mark:                                                                                      | Subscription ID                                                                                         |
| `cancel_at`                                                                                             | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `cancel_at_period_end`                                                                                  | *Optional[bool]*                                                                                        | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `parent_subscription_id`                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | ParentSubscriptionID sets or clears the parent subscription. Omit to leave unchanged; send "" to clear. |
| `status`                                                                                                | [Optional[models.TypesSubscriptionStatus]](../../models/typessubscriptionstatus.md)                     | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |

### Response

**[models.DtoSubscriptionResponse](../../models/dtosubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## activate_subscription

Use when turning a draft subscription live (e.g. after collecting payment or completing setup). Once activated, billing and entitlements apply.

### Example Usage

<!-- UsageSnippet language="python" operationID="activateSubscription" method="post" path="/subscriptions/{id}/activate" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.activate_subscription(id="<id>", start_date="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `id`                                                                  | *str*                                                                 | :heavy_check_mark:                                                    | Subscription ID                                                       |
| `start_date`                                                          | *str*                                                                 | :heavy_check_mark:                                                    | start_date is the new start date for the subscription when activating |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[models.DtoSubscriptionResponse](../../models/dtosubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription_addon_associations

Use when listing which add-ons are currently attached to a subscription (e.g. for display or editing).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionAddonAssociations" method="get" path="/subscriptions/{id}/addons/associations" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_addon_associations(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.DtoAddonAssociationResponse]](../../models/.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## cancel_subscription

Use when a customer churns or downgrades. Supports immediate or end-of-period cancellation and proration. Ideal for self-serve or support-driven cancellations.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelSubscription" method="post" path="/subscriptions/{id}/cancel" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.cancel_subscription(id="<id>", cancellation_type="immediate")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                        | *str*                                                                                                       | :heavy_check_mark:                                                                                          | Subscription ID                                                                                             |
| `cancellation_type`                                                                                         | [models.TypesCancellationType](../../models/typescancellationtype.md)                                       | :heavy_check_mark:                                                                                          | N/A                                                                                                         |
| `cancel_immediately_inovice_policy`                                                                         | [Optional[models.TypesCancelImmediatelyInvoicePolicy]](../../models/typescancelimmediatelyinvoicepolicy.md) | :heavy_minus_sign:                                                                                          | N/A                                                                                                         |
| `proration_behavior`                                                                                        | [Optional[models.TypesProrationBehavior]](../../models/typesprorationbehavior.md)                           | :heavy_minus_sign:                                                                                          | N/A                                                                                                         |
| `reason`                                                                                                    | *Optional[str]*                                                                                             | :heavy_minus_sign:                                                                                          | Reason for cancellation (for audit and business intelligence)                                               |
| `retries`                                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                            | :heavy_minus_sign:                                                                                          | Configuration to override the default retry behavior of the client.                                         |

### Response

**[models.DtoCancelSubscriptionResponse](../../models/dtocancelsubscriptionresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## execute_subscription_change

Use when applying a plan change (e.g. upgrade or downgrade). Executes proration and generates invoice or credit as needed.

### Example Usage

<!-- UsageSnippet language="python" operationID="executeSubscriptionChange" method="post" path="/subscriptions/{id}/change/execute" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.execute_subscription_change(id="<id>", billing_cadence="RECURRING", billing_cycle="anniversary", billing_period="QUARTERLY", proration_behavior="create_prorations", target_plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `id`                                                                       | *str*                                                                      | :heavy_check_mark:                                                         | Subscription ID                                                            |
| `billing_cadence`                                                          | [models.TypesBillingCadence](../../models/typesbillingcadence.md)          | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_cycle`                                                            | [models.TypesBillingCycle](../../models/typesbillingcycle.md)              | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_period`                                                           | [models.TypesBillingPeriod](../../models/typesbillingperiod.md)            | :heavy_check_mark:                                                         | N/A                                                                        |
| `proration_behavior`                                                       | [models.TypesProrationBehavior](../../models/typesprorationbehavior.md)    | :heavy_check_mark:                                                         | N/A                                                                        |
| `target_plan_id`                                                           | *str*                                                                      | :heavy_check_mark:                                                         | target_plan_id is the ID of the new plan to change to (required)           |
| `billing_period_count`                                                     | *Optional[int]*                                                            | :heavy_minus_sign:                                                         | billing_period_count is the billing period count for the new subscription  |
| `change_at`                                                                | [Optional[models.TypesScheduleType]](../../models/typesscheduletype.md)    | :heavy_minus_sign:                                                         | N/A                                                                        |
| `metadata`                                                                 | Dict[str, *str*]                                                           | :heavy_minus_sign:                                                         | metadata contains additional key-value pairs for storing extra information |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[models.DtoSubscriptionChangeExecuteResponse](../../models/dtosubscriptionchangeexecuteresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## preview_subscription_change

Use when showing a customer the cost of a plan change before they confirm (e.g. upgrade/downgrade preview with proration).

### Example Usage

<!-- UsageSnippet language="python" operationID="previewSubscriptionChange" method="post" path="/subscriptions/{id}/change/preview" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.preview_subscription_change(id="<id>", billing_cadence="RECURRING", billing_cycle="calendar", billing_period="HALF_YEARLY", proration_behavior="create_prorations", target_plan_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `id`                                                                       | *str*                                                                      | :heavy_check_mark:                                                         | Subscription ID                                                            |
| `billing_cadence`                                                          | [models.TypesBillingCadence](../../models/typesbillingcadence.md)          | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_cycle`                                                            | [models.TypesBillingCycle](../../models/typesbillingcycle.md)              | :heavy_check_mark:                                                         | N/A                                                                        |
| `billing_period`                                                           | [models.TypesBillingPeriod](../../models/typesbillingperiod.md)            | :heavy_check_mark:                                                         | N/A                                                                        |
| `proration_behavior`                                                       | [models.TypesProrationBehavior](../../models/typesprorationbehavior.md)    | :heavy_check_mark:                                                         | N/A                                                                        |
| `target_plan_id`                                                           | *str*                                                                      | :heavy_check_mark:                                                         | target_plan_id is the ID of the new plan to change to (required)           |
| `billing_period_count`                                                     | *Optional[int]*                                                            | :heavy_minus_sign:                                                         | billing_period_count is the billing period count for the new subscription  |
| `change_at`                                                                | [Optional[models.TypesScheduleType]](../../models/typesscheduletype.md)    | :heavy_minus_sign:                                                         | N/A                                                                        |
| `metadata`                                                                 | Dict[str, *str*]                                                           | :heavy_minus_sign:                                                         | metadata contains additional key-value pairs for storing extra information |
| `retries`                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)           | :heavy_minus_sign:                                                         | Configuration to override the default retry behavior of the client.        |

### Response

**[models.DtoSubscriptionChangePreviewResponse](../../models/dtosubscriptionchangepreviewresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription_entitlements

Use when checking what features or limits a subscription has (e.g. entitlement checks or feature gating). Optional feature_ids to filter.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionEntitlements" method="get" path="/subscriptions/{id}/entitlements" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `feature_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | Feature IDs to filter by                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSubscriptionEntitlementsResponse](../../models/dtosubscriptionentitlementsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription_upcoming_grants

Use when showing upcoming or pending credits for a subscription (e.g. in a portal or for forecasting).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionUpcomingGrants" method="get" path="/subscriptions/{id}/grants/upcoming" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_upcoming_grants(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListCreditGrantApplicationsResponse](../../models/dtolistcreditgrantapplicationsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_subscription_line_item

Use when adding a new charge or seat to a subscription (e.g. extra seat or one-time add). Supports price_id or inline price.

### Example Usage

<!-- UsageSnippet language="python" operationID="createSubscriptionLineItem" method="post" path="/subscriptions/{id}/lineitems" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.create_subscription_line_item(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                 | Type                                                                                                                      | Required                                                                                                                  | Description                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                      | *str*                                                                                                                     | :heavy_check_mark:                                                                                                        | Subscription ID                                                                                                           |
| `commitment_amount`                                                                                                       | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | Commitment fields                                                                                                         |
| `commitment_duration`                                                                                                     | [Optional[models.TypesBillingPeriod]](../../models/typesbillingperiod.md)                                                 | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_overage_factor`                                                                                               | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_quantity`                                                                                                     | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_true_up_enabled`                                                                                              | *Optional[bool]*                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_type`                                                                                                         | [Optional[models.TypesCommitmentType]](../../models/typescommitmenttype.md)                                               | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `commitment_windowed`                                                                                                     | *Optional[bool]*                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `display_name`                                                                                                            | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `end_date`                                                                                                                | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `metadata`                                                                                                                | Dict[str, *str*]                                                                                                          | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `price`                                                                                                                   | [Optional[models.DtoSubscriptionPriceCreateRequest]](../../models/dtosubscriptionpricecreaterequest.md)                   | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `price_id`                                                                                                                | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | PriceID references an existing price (plan, addon, or subscription-scoped). Exactly one of price_id or price must be set. |
| `quantity`                                                                                                                | *Optional[float]*                                                                                                         | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `start_date`                                                                                                              | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `subscription_phase_id`                                                                                                   | *Optional[str]*                                                                                                           | :heavy_minus_sign:                                                                                                        | N/A                                                                                                                       |
| `retries`                                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                          | :heavy_minus_sign:                                                                                                        | Configuration to override the default retry behavior of the client.                                                       |

### Response

**[models.DtoSubscriptionLineItemResponse](../../models/dtosubscriptionlineitemresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## pause_subscription

Use when temporarily stopping a subscription (e.g. customer hold or seasonal pause). Billing and access pause; resume when ready.

### Example Usage

<!-- UsageSnippet language="python" operationID="pauseSubscription" method="post" path="/subscriptions/{id}/pause" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.pause_subscription(id="<id>", pause_mode="scheduled")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                         | Type                                                                                                                                                                                              | Required                                                                                                                                                                                          | Description                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                              | *str*                                                                                                                                                                                             | :heavy_check_mark:                                                                                                                                                                                | Subscription ID                                                                                                                                                                                   |
| `pause_mode`                                                                                                                                                                                      | [models.TypesPauseMode](../../models/typespausemode.md)                                                                                                                                           | :heavy_check_mark:                                                                                                                                                                                | N/A                                                                                                                                                                                               |
| `dry_run`                                                                                                                                                                                         | *Optional[bool]*                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                | Whether to perform a dry run<br/>@Description If true, validates the request and shows impact without actually pausing the subscription<br/>@Example false                                        |
| `metadata`                                                                                                                                                                                        | Dict[str, *str*]                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                | Additional metadata as key-value pairs<br/>@Description Optional metadata for storing additional information about the pause<br/>@Example {"requested_by": "customer", "channel": "support_ticket"} |
| `pause_days`                                                                                                                                                                                      | *Optional[int]*                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                | Duration of the pause in days<br/>@Description Number of days to pause the subscription. Cannot be used together with pause_end. Must be greater than 0<br/>@Example 30                           |
| `pause_end`                                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                | End date for the subscription pause<br/>@Description ISO 8601 timestamp when the pause should end. Cannot be used together with pause_days. Must be after pause_start<br/>@Example "2024-02-15T00:00:00Z" |
| `pause_start`                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                | Start date for the subscription pause<br/>@Description ISO 8601 timestamp when the pause should begin. Required when pause_mode is "scheduled"<br/>@Example "2024-01-15T00:00:00Z"                |
| `reason`                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                | Reason for pausing the subscription<br/>@Description Optional reason for the pause. Maximum 255 characters<br/>@Example "Customer requested temporary suspension"                                 |
| `retries`                                                                                                                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                | Configuration to override the default retry behavior of the client.                                                                                                                               |

### Response

**[models.DtoSubscriptionPauseResponse](../../models/dtosubscriptionpauseresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## list_subscription_pauses

Use when showing pause history for a subscription (e.g. support or audit). Returns all past and future pauses.

### Example Usage

<!-- UsageSnippet language="python" operationID="listSubscriptionPauses" method="get" path="/subscriptions/{id}/pauses" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.list_subscription_pauses(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.DtoListSubscriptionPausesResponse]](../../models/.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## resume_subscription

Use when reactivating a paused subscription (e.g. end of hold). Billing and access resume from the resume date.

### Example Usage

<!-- UsageSnippet language="python" operationID="resumeSubscription" method="post" path="/subscriptions/{id}/resume" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.resume_subscription(id="<id>", resume_mode="auto")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                        | Type                                                                                                                                                                                             | Required                                                                                                                                                                                         | Description                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`                                                                                                                                                                                             | *str*                                                                                                                                                                                            | :heavy_check_mark:                                                                                                                                                                               | Subscription ID                                                                                                                                                                                  |
| `resume_mode`                                                                                                                                                                                    | [models.TypesResumeMode](../../models/typesresumemode.md)                                                                                                                                        | :heavy_check_mark:                                                                                                                                                                               | N/A                                                                                                                                                                                              |
| `dry_run`                                                                                                                                                                                        | *Optional[bool]*                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                               | Whether to perform a dry run<br/>@Description If true, validates the request and shows impact without actually resuming the subscription<br/>@Example false                                      |
| `metadata`                                                                                                                                                                                       | Dict[str, *str*]                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                               | Additional metadata as key-value pairs<br/>@Description Optional metadata for storing additional information about the resume operation<br/>@Example {"resumed_by": "admin", "reason": "issue_resolved"} |
| `retries`                                                                                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                               | Configuration to override the default retry behavior of the client.                                                                                                                              |

### Response

**[models.DtoSubscriptionPauseResponse](../../models/dtosubscriptionpauseresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_subscription_v2

Use when you need a subscription with related data (line items, prices, plan). Supports expand for detailed payloads without extra round-trips.

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionV2" method="get" path="/subscriptions/{id}/v2" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_v2(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                              | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `id`                                                                                   | *str*                                                                                  | :heavy_check_mark:                                                                     | Subscription ID                                                                        |
| `expand`                                                                               | *Optional[str]*                                                                        | :heavy_minus_sign:                                                                     | Comma-separated list of fields to expand (e.g., 'subscription_line_items,prices,plan') |
| `retries`                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                       | :heavy_minus_sign:                                                                     | Configuration to override the default retry behavior of the client.                    |

### Response

**[models.DtoSubscriptionResponseV2](../../models/dtosubscriptionresponsev2.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## list_all_subscription_schedules

Use when listing or searching scheduled changes across subscriptions (e.g. admin view). Returns schedules with optional filtering.

### Example Usage

<!-- UsageSnippet language="python" operationID="listAllSubscriptionSchedules" method="get" path="/v1/subscription-schedules" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.list_all_subscription_schedules()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `pending_only`                                                      | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Filter to pending schedules only                                    |
| `subscription_id`                                                   | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Filter by subscription ID                                           |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Limit results                                                       |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | Offset for pagination                                               |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoGetPendingSchedulesResponse](../../models/dtogetpendingschedulesresponse.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## get_subscription_schedule

Use when you need to load a single scheduled change (e.g. to show when a plan change or renewal takes effect).

### Example Usage

<!-- UsageSnippet language="python" operationID="getSubscriptionSchedule" method="get" path="/v1/subscription-schedules/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.get_subscription_schedule(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Schedule ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSubscriptionScheduleResponse](../../models/dtosubscriptionscheduleresponse.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## cancel_subscription_schedule

Use when cancelling a scheduled change (e.g. customer changed mind). Identify by schedule ID in path or by subscription ID + schedule type in body.

### Example Usage

<!-- UsageSnippet language="python" operationID="cancelSubscriptionSchedule" method="post" path="/v1/subscriptions/schedules/{schedule_id}/cancel" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.cancel_subscription_schedule(schedule_id_param="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `schedule_id_param`                                                                                          | *str*                                                                                                        | :heavy_check_mark:                                                                                           | Schedule ID (optional if using request body)                                                                 |
| `schedule_id`                                                                                                | *Optional[str]*                                                                                              | :heavy_minus_sign:                                                                                           | schedule_id is the ID of the schedule to cancel (optional if subscription_id and schedule_type are provided) |
| `schedule_type`                                                                                              | [Optional[models.TypesSubscriptionScheduleChangeType]](../../models/typessubscriptionschedulechangetype.md)  | :heavy_minus_sign:                                                                                           | N/A                                                                                                          |
| `subscription_id`                                                                                            | *Optional[str]*                                                                                              | :heavy_minus_sign:                                                                                           | subscription_id is the ID of the subscription (required if schedule_id is not provided)                      |
| `retries`                                                                                                    | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                             | :heavy_minus_sign:                                                                                           | Configuration to override the default retry behavior of the client.                                          |

### Response

**[models.DtoCancelScheduleResponse](../../models/dtocancelscheduleresponse.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## list_subscription_schedules

Use when listing scheduled changes for a subscription (e.g. upcoming plan change or renewal). Returns all schedules for that subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="listSubscriptionSchedules" method="get" path="/v1/subscriptions/{subscription_id}/schedules" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.subscriptions.list_subscription_schedules(subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `subscription_id`                                                   | *str*                                                               | :heavy_check_mark:                                                  | Subscription ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoGetPendingSchedulesResponse](../../models/dtogetpendingschedulesresponse.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |