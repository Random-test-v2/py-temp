# Invoices

## Overview

### Available Operations

* [get_customer_invoice_summary](#get_customer_invoice_summary) - Get customer invoice summary
* [create_invoice](#create_invoice) - Create one-off invoice
* [get_invoice_preview](#get_invoice_preview) - Get invoice preview
* [query_invoice](#query_invoice) - Query invoices
* [get_invoice](#get_invoice) - Get invoice
* [update_invoice](#update_invoice) - Update invoice
* [trigger_invoice_comms_webhook](#trigger_invoice_comms_webhook) - Trigger invoice communication webhook
* [finalize_invoice](#finalize_invoice) - Finalize invoice
* [update_invoice_payment_status](#update_invoice_payment_status) - Update invoice payment status
* [attempt_invoice_payment](#attempt_invoice_payment) - Attempt invoice payment
* [get_invoice_pdf](#get_invoice_pdf) - Get invoice PDF
* [recalculate_invoice](#recalculate_invoice) - Recalculate invoice
* [void_invoice](#void_invoice) - Void invoice

## get_customer_invoice_summary

Use when showing a customer's invoice overview (e.g. billing portal or balance summary). Includes totals and multi-currency breakdown.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerInvoiceSummary" method="get" path="/customers/{id}/invoices/summary" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.get_customer_invoice_summary(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCustomerMultiCurrencyInvoiceSummary](../../models/dtocustomermulticurrencyinvoicesummary.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_invoice

Use when creating a manual or one-off invoice (e.g. custom charge or non-recurring billing). Invoice is created in draft; finalize when ready.

### Example Usage

<!-- UsageSnippet language="python" operationID="createInvoice" method="post" path="/invoices" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.create_invoice(amount_due="<value>", currency="Surinam Dollar", customer_id="<id>", subtotal="<value>", total="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `amount_due`                                                                                       | *str*                                                                                              | :heavy_check_mark:                                                                                 | amount_due is the total amount that needs to be paid for this invoice                              |
| `currency`                                                                                         | *str*                                                                                              | :heavy_check_mark:                                                                                 | currency is the three-letter ISO currency code (e.g., USD, EUR) for the invoice                    |
| `customer_id`                                                                                      | *str*                                                                                              | :heavy_check_mark:                                                                                 | customer_id is the unique identifier of the customer this invoice belongs to                       |
| `subtotal`                                                                                         | *str*                                                                                              | :heavy_check_mark:                                                                                 | subtotal is the amount before taxes and discounts are applied                                      |
| `total`                                                                                            | *str*                                                                                              | :heavy_check_mark:                                                                                 | total is the total amount of the invoice including taxes and discounts                             |
| `amount_paid`                                                                                      | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | amount_paid is the amount that has been paid towards this invoice                                  |
| `billing_period`                                                                                   | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | billing_period is the period this invoice covers (e.g., "monthly", "yearly")                       |
| `billing_reason`                                                                                   | [Optional[models.TypesInvoiceBillingReason]](../../models/typesinvoicebillingreason.md)            | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `coupons`                                                                                          | List[*str*]                                                                                        | :heavy_minus_sign:                                                                                 | coupons                                                                                            |
| `description`                                                                                      | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | description is an optional text description of the invoice                                         |
| `due_date`                                                                                         | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | due_date is the date by which payment is expected                                                  |
| `idempotency_key`                                                                                  | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | idempotency_key is an optional key used to prevent duplicate invoice creation                      |
| `invoice_coupons`                                                                                  | List[[models.DtoInvoiceCoupon](../../models/dtoinvoicecoupon.md)]                                  | :heavy_minus_sign:                                                                                 | Invoice Coupons                                                                                    |
| `invoice_number`                                                                                   | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | invoice_number is an optional human-readable identifier for the invoice                            |
| `invoice_pdf_url`                                                                                  | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | invoice_pdf_url is the URL where customers can download the PDF version of this invoice            |
| `invoice_status`                                                                                   | [Optional[models.TypesInvoiceStatus]](../../models/typesinvoicestatus.md)                          | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `invoice_type`                                                                                     | [Optional[models.TypesInvoiceType]](../../models/typesinvoicetype.md)                              | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `line_item_coupons`                                                                                | List[[models.DtoInvoiceLineItemCoupon](../../models/dtoinvoicelineitemcoupon.md)]                  | :heavy_minus_sign:                                                                                 | Invoice Line Item Coupons                                                                          |
| `line_items`                                                                                       | List[[models.DtoCreateInvoiceLineItemRequest](../../models/dtocreateinvoicelineitemrequest.md)]    | :heavy_minus_sign:                                                                                 | line_items contains the individual items that make up this invoice                                 |
| `metadata`                                                                                         | Dict[str, *str*]                                                                                   | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `payment_status`                                                                                   | [Optional[models.TypesPaymentStatus]](../../models/typespaymentstatus.md)                          | :heavy_minus_sign:                                                                                 | N/A                                                                                                |
| `period_end`                                                                                       | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | period_end is the end date of the billing period                                                   |
| `period_start`                                                                                     | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | period_start is the start date of the billing period                                               |
| `prepared_tax_rates`                                                                               | List[[models.DtoTaxRateResponse](../../models/dtotaxrateresponse.md)]                              | :heavy_minus_sign:                                                                                 | prepared_tax_rates contains the tax rates pre-resolved by the caller (e.g., billing service)       |
| `subscription_id`                                                                                  | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | subscription_id is the optional unique identifier of the subscription associated with this invoice |
| `tax_rate_overrides`                                                                               | List[[models.DtoTaxRateOverride](../../models/dtotaxrateoverride.md)]                              | :heavy_minus_sign:                                                                                 | tax_rate_overrides is the tax rate overrides to be applied to the invoice                          |
| `tax_rates`                                                                                        | List[*str*]                                                                                        | :heavy_minus_sign:                                                                                 | tax_rates                                                                                          |
| `total_prepaid_applied`                                                                            | *Optional[str]*                                                                                    | :heavy_minus_sign:                                                                                 | total_prepaid_applied is the total amount of prepaid applied to this invoice.                      |
| `retries`                                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                   | :heavy_minus_sign:                                                                                 | Configuration to override the default retry behavior of the client.                                |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_invoice_preview

Use when showing a customer what they will be charged (e.g. preview before checkout or plan change). No invoice is created.

### Example Usage

<!-- UsageSnippet language="python" operationID="getInvoicePreview" method="post" path="/invoices/preview" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.get_invoice_preview(subscription_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `subscription_id`                                                                   | *str*                                                                               | :heavy_check_mark:                                                                  | subscription_id is the unique identifier of the subscription to preview invoice for |
| `period_end`                                                                        | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | period_end is the optional end date of the period to preview                        |
| `period_start`                                                                      | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | period_start is the optional start date of the period to preview                    |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_invoice

Use when listing or searching invoices (e.g. admin view or customer history). Returns a paginated list; supports filtering by customer, status, date range.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryInvoice" method="post" path="/invoices/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.query_invoice()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                        | Type                                                                                                                                                                             | Required                                                                                                                                                                         | Description                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `amount_due_gt`                                                                                                                                                                  | *Optional[float]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                               | amount_due_gt filters invoices with a total amount due greater than the specified value<br/>Useful for finding invoices above a certain threshold or identifying high-value invoices |
| `amount_remaining_gt`                                                                                                                                                            | *Optional[float]*                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                               | amount_remaining_gt filters invoices with an outstanding balance greater than the specified value<br/>Useful for finding invoices that still have significant unpaid amounts     |
| `customer_id`                                                                                                                                                                    | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | customer_id filters invoices for a specific customer using FlexPrice's internal customer ID<br/>This is the ID returned by FlexPrice when creating or retrieving customers       |
| `end_time`                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `expand`                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `external_customer_id`                                                                                                                                                           | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | external_customer_id filters invoices for a customer using your system's customer identifier<br/>This is the ID you provided when creating the customer in FlexPrice             |
| `filters`                                                                                                                                                                        | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]                                                                                                        | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `invoice_ids`                                                                                                                                                                    | List[*str*]                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                               | invoice_ids restricts results to invoices with the specified IDs<br/>Use this to retrieve specific invoices when you know their exact identifiers                                |
| `invoice_status`                                                                                                                                                                 | List[[models.TypesInvoiceStatus](../../models/typesinvoicestatus.md)]                                                                                                            | :heavy_minus_sign:                                                                                                                                                               | invoice_status filters by the current state of invoices in their lifecycle<br/>Multiple statuses can be specified to include invoices in any of the listed states                |
| `invoice_type`                                                                                                                                                                   | [Optional[models.TypesInvoiceType]](../../models/typesinvoicetype.md)                                                                                                            | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `limit`                                                                                                                                                                          | *Optional[int]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `offset`                                                                                                                                                                         | *Optional[int]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `order`                                                                                                                                                                          | [Optional[models.TypesInvoiceFilterOrder]](../../models/typesinvoicefilterorder.md)                                                                                              | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `payment_status`                                                                                                                                                                 | List[[models.TypesPaymentStatus](../../models/typespaymentstatus.md)]                                                                                                            | :heavy_minus_sign:                                                                                                                                                               | payment_status filters by the payment state of invoices<br/>Multiple statuses can be specified to include invoices with any of the listed payment states                         |
| `period_end_gte`                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | period_end_gte filters invoices with period_end >= value                                                                                                                         |
| `period_end_lte`                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | period_end_lte filters invoices with period_end <= value                                                                                                                         |
| `period_start_gte`                                                                                                                                                               | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | period_start_gte filters invoices with period_start >= value                                                                                                                     |
| `period_start_lte`                                                                                                                                                               | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | period_start_lte filters invoices with period_start <= value                                                                                                                     |
| `skip_line_items`                                                                                                                                                                | *Optional[bool]*                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                               | SkipLineItems if true, will not include line items in the response                                                                                                               |
| `sort`                                                                                                                                                                           | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                                                                                                            | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `start_time`                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `status`                                                                                                                                                                         | [Optional[models.TypesStatus]](../../models/typesstatus.md)                                                                                                                      | :heavy_minus_sign:                                                                                                                                                               | N/A                                                                                                                                                                              |
| `subscription_id`                                                                                                                                                                | *Optional[str]*                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                               | subscription_id filters invoices generated for a specific subscription<br/>Only returns invoices that were created as part of the specified subscription's billing               |
| `retries`                                                                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                 | :heavy_minus_sign:                                                                                                                                                               | Configuration to override the default retry behavior of the client.                                                                                                              |

### Response

**[models.DtoListInvoicesResponse](../../models/dtolistinvoicesresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_invoice

Use when loading an invoice for display or editing (e.g. portal or reconciliation). Supports group_by for usage breakdown and force_runtime_recalculation.

### Example Usage

<!-- UsageSnippet language="python" operationID="getInvoice" method="get" path="/invoices/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.get_invoice(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `id`                                                                                    | *str*                                                                                   | :heavy_check_mark:                                                                      | Invoice ID                                                                              |
| `expand_by_source`                                                                      | *Optional[bool]*                                                                        | :heavy_minus_sign:                                                                      | Include source-level price breakdown for usage line items (legacy)                      |
| `group_by`                                                                              | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | Group usage breakdown by specified fields (e.g., source, feature_id, properties.org_id) |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 404                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_invoice

Use when updating invoice metadata or due date (e.g. PDF URL, net terms). For paid invoices only safe fields can be updated.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateInvoice" method="put" path="/invoices/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.update_invoice(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `id`                                                                                    | *str*                                                                                   | :heavy_check_mark:                                                                      | Invoice ID                                                                              |
| `due_date`                                                                              | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `invoice_pdf_url`                                                                       | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | invoice_pdf_url is the URL where customers can download the PDF version of this invoice |
| `metadata`                                                                              | Dict[str, *str*]                                                                        | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## trigger_invoice_comms_webhook

Use when sending an invoice to the customer (e.g. trigger email or Slack). Payload includes full invoice details for your integration.

### Example Usage

<!-- UsageSnippet language="python" operationID="triggerInvoiceCommsWebhook" method="post" path="/invoices/{id}/comms/trigger" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.trigger_invoice_comms_webhook(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## finalize_invoice

Use when locking an invoice for payment (e.g. after review). Once finalized, line items are locked; invoice can be paid or voided.

### Example Usage

<!-- UsageSnippet language="python" operationID="finalizeInvoice" method="post" path="/invoices/{id}/finalize" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.finalize_invoice(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_invoice_payment_status

Use when reconciling payment status from an external gateway or manual entry (e.g. mark paid after bank confirmation).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateInvoicePaymentStatus" method="put" path="/invoices/{id}/payment" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.update_invoice_payment_status(id="<id>", payment_status="INITIATED")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `payment_status`                                                    | [models.TypesPaymentStatus](../../models/typespaymentstatus.md)     | :heavy_check_mark:                                                  | N/A                                                                 |
| `amount`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | amount is the optional payment amount to record                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## attempt_invoice_payment

Use when paying an invoice with the customer's wallet balance (e.g. prepaid credits or balance applied at checkout).

### Example Usage

<!-- UsageSnippet language="python" operationID="attemptInvoicePayment" method="post" path="/invoices/{id}/payment/attempt" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.attempt_invoice_payment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_invoice_pdf

Use when delivering an invoice PDF to the customer (e.g. email attachment or download). Use url=true for a presigned URL instead of binary.

### Example Usage

<!-- UsageSnippet language="python" operationID="getInvoicePdf" method="get" path="/invoices/{id}/pdf" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.get_invoice_pdf(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `url`                                                               | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Return presigned URL from s3 instead of PDF                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[httpx.Response](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## recalculate_invoice

Use when subscription or usage data changed and you need to refresh a draft invoice before finalizing. Optional finalize=true to lock after recalc.

### Example Usage

<!-- UsageSnippet language="python" operationID="recalculateInvoice" method="post" path="/invoices/{id}/recalculate" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.recalculate_invoice(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `finalize`                                                          | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Whether to finalize the invoice after recalculation (default: true) |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoInvoiceResponse](../../models/dtoinvoiceresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## void_invoice

Use when cancelling an invoice (e.g. order cancelled or duplicate). Only unpaid invoices can be voided.

### Example Usage

<!-- UsageSnippet language="python" operationID="voidInvoice" method="post" path="/invoices/{id}/void" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.invoices.void_invoice(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Invoice ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |