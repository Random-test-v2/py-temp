# Payments

## Overview

### Available Operations

* [list_payments](#list_payments) - List payments
* [create_payment](#create_payment) - Create payment
* [get_payment](#get_payment) - Get payment
* [update_payment](#update_payment) - Update payment
* [delete_payment](#delete_payment) - Delete payment
* [process_payment](#process_payment) - Process payment

## list_payments

Use when listing or searching payments (e.g. reconciliation UI or customer payment history). Returns a paginated list; supports filtering by customer, invoice, status.

### Example Usage

<!-- UsageSnippet language="python" operationID="listPayments" method="get" path="/payments" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.list_payments()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `currency`                                                                | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `destination_id`                                                          | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `destination_type`                                                        | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `end_time`                                                                | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `expand`                                                                  | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `gateway_payment_id`                                                      | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `gateway_tracking_id`                                                     | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | For filtering by gateway tracking ID                                      |
| `limit`                                                                   | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `offset`                                                                  | *Optional[int]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `order`                                                                   | [Optional[models.ListPaymentsOrder]](../../models/listpaymentsorder.md)   | :heavy_minus_sign:                                                        | N/A                                                                       |
| `payment_gateway`                                                         | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `payment_ids`                                                             | List[*str*]                                                               | :heavy_minus_sign:                                                        | N/A                                                                       |
| `payment_method_type`                                                     | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `payment_status`                                                          | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `sort`                                                                    | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `start_time`                                                              | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `status`                                                                  | [Optional[models.ListPaymentsStatus]](../../models/listpaymentsstatus.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.DtoListPaymentsResponse](../../models/dtolistpaymentsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## create_payment

Use when recording a payment against an invoice (e.g. after receiving funds via a gateway or manual entry).

### Example Usage

<!-- UsageSnippet language="python" operationID="createPayment" method="post" path="/payments" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.create_payment(amount="883.46", currency="CFP Franc", destination_id="<id>", destination_type="INVOICE", payment_method_type="OFFLINE", process_payment=True, save_card_and_make_default=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `amount`                                                                            | *str*                                                                               | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `currency`                                                                          | *str*                                                                               | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `destination_id`                                                                    | *str*                                                                               | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `destination_type`                                                                  | [models.TypesPaymentDestinationType](../../models/typespaymentdestinationtype.md)   | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `payment_method_type`                                                               | [models.TypesPaymentMethodType](../../models/typespaymentmethodtype.md)             | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `cancel_url`                                                                        | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `idempotency_key`                                                                   | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `metadata`                                                                          | Dict[str, *str*]                                                                    | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `payment_gateway`                                                                   | [Optional[models.TypesPaymentGatewayType]](../../models/typespaymentgatewaytype.md) | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `payment_method_id`                                                                 | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `process_payment`                                                                   | *Optional[bool]*                                                                    | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `save_card_and_make_default`                                                        | *Optional[bool]*                                                                    | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `success_url`                                                                       | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.DtoPaymentResponse](../../models/dtopaymentresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_payment

Use when you need to load a single payment (e.g. for a receipt view or reconciliation).

### Example Usage

<!-- UsageSnippet language="python" operationID="getPayment" method="get" path="/payments/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.get_payment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Payment ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPaymentResponse](../../models/dtopaymentresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_payment

Use when updating payment status or metadata (e.g. after reconciliation or adding a reference).

### Example Usage

<!-- UsageSnippet language="python" operationID="updatePayment" method="put" path="/payments/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.update_payment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Payment ID                                                          |
| `error_message`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `failed_at`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `gateway_payment_id`                                                | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `payment_gateway`                                                   | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `payment_method_id`                                                 | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `payment_status`                                                    | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `succeeded_at`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPaymentResponse](../../models/dtopaymentresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_payment

Use when removing or voiding a payment record (e.g. correcting erroneous entries). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deletePayment" method="delete" path="/payments/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.delete_payment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Payment ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## process_payment

Use when you need to charge or process a payment (e.g. trigger the payment provider to capture funds). Returns updated payment with status.

### Example Usage

<!-- UsageSnippet language="python" operationID="processPayment" method="post" path="/payments/{id}/process" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.payments.process_payment(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Payment ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPaymentResponse](../../models/dtopaymentresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |