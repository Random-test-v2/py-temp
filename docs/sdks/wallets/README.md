# Wallets

## Overview

### Available Operations

* [get_customer_wallets](#get_customer_wallets) - Get Customer Wallets
* [get_wallets_by_customer_id](#get_wallets_by_customer_id) - Get wallets by customer ID
* [create_wallet](#create_wallet) - Create a new wallet
* [query_wallet](#query_wallet) - Query wallets
* [query_wallet_transaction](#query_wallet_transaction) - Query wallet transactions
* [get_wallet](#get_wallet) - Get wallet
* [update_wallet](#update_wallet) - Update a wallet
* [get_wallet_balance](#get_wallet_balance) - Get wallet balance
* [terminate_wallet](#terminate_wallet) - Terminate a wallet
* [top_up_wallet](#top_up_wallet) - Top up wallet
* [get_wallet_transactions](#get_wallet_transactions) - Get wallet transactions

## get_customer_wallets

Use when resolving wallets by external customer id or lookup key (e.g. from your app's user id). Supports optional real-time balance and expand.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerWallets" method="get" path="/customers/wallets" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.get_customer_wallets(from_cache=False, include_real_time_balance=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `expand`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `from_cache`                                                        | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `id`                                                                | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `include_real_time_balance`                                         | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `lookup_key`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.DtoWalletResponse]](../../models/.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_wallets_by_customer_id

Use when showing a customer's wallets (e.g. balance overview by currency or in a billing portal). Supports optional expand for balance breakdown.

### Example Usage

<!-- UsageSnippet language="python" operationID="getWalletsByCustomerId" method="get" path="/customers/{id}/wallets" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.get_wallets_by_customer_id(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[List[models.DtoWalletResponse]](../../models/.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## create_wallet

Use when giving a customer a prepaid or credit balance (e.g. prepaid plans or promotional credits).

### Example Usage

<!-- UsageSnippet language="python" operationID="createWallet" method="post" path="/wallets" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.create_wallet(currency="Seychelles Rupee", conversion_rate="1", initial_credits_to_load="0")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `currency`                                                                                                                                                                                                                                                               | *str*                                                                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `alert_settings`                                                                                                                                                                                                                                                         | [Optional[models.TypesAlertSettings]](../../models/typesalertsettings.md)                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `auto_topup`                                                                                                                                                                                                                                                             | [Optional[models.TypesAutoTopup]](../../models/typesautotopup.md)                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `conversion_rate`                                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | amount in the currency =  number of credits * conversion_rate<br/>ex if conversion_rate is 1, then 1 USD = 1 credit<br/>ex if conversion_rate is 2, then 1 USD = 0.5 credits<br/>ex if conversion_rate is 0.5, then 1 USD = 2 credits                                    |
| `customer_id`                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `description`                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `external_customer_id`                                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | external_customer_id is the customer id in the external system                                                                                                                                                                                                           |
| `initial_credits_expiry_date_utc`                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | initial_credits_expiry_date_utc is the expiry date in UTC timezone (optional to set nil means no expiry)<br/>ex 2025-01-01 00:00:00 UTC                                                                                                                                  |
| `initial_credits_to_load`                                                                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | initial_credits_to_load is the number of credits to load to the wallet<br/>if not provided, the wallet will be created with 0 balance<br/>NOTE: this is not the amount in the currency, but the number of credits                                                        |
| `initial_credits_to_load_expiry_date`                                                                                                                                                                                                                                    | *Optional[int]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | initial_credits_to_load_expiry_date YYYYMMDD format in UTC timezone (optional to set nil means no expiry)<br/>for ex 20250101 means the credits will expire on 2025-01-01 00:00:00 UTC<br/>hence they will be available for use until 2024-12-31 23:59:59 UTC            |
| `metadata`                                                                                                                                                                                                                                                               | Dict[str, *str*]                                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `price_unit`                                                                                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | price_unit is the code of the price unit to use for wallet creation<br/>If provided, the price unit will be used to set the currency and conversion rate of the wallet:<br/>- currency: set to price unit's base_currency<br/>- conversion_rate: set to price unit's conversion_rate |
| `topup_conversion_rate`                                                                                                                                                                                                                                                  | *Optional[str]*                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                       | topup_conversion_rate is the conversion rate for the topup to the currency<br/>ex if topup_conversion_rate is 1, then 1 USD = 1 credit<br/>ex if topup_conversion_rate is 2, then 1 USD = 0.5 credits<br/>ex if topup_conversion_rate is 0.5, then 1 USD = 2 credits     |
| `wallet_type`                                                                                                                                                                                                                                                            | [Optional[models.TypesWalletType]](../../models/typeswallettype.md)                                                                                                                                                                                                      | :heavy_minus_sign:                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                      |
| `retries`                                                                                                                                                                                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                       | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                      |

### Response

**[models.DtoWalletResponse](../../models/dtowalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## query_wallet

Use when listing or searching wallets (e.g. admin view or reporting). Returns a paginated list; supports filtering by customer and status.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryWallet" method="post" path="/wallets/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.query_wallet()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `alert_enabled`                                                                   | *Optional[bool]*                                                                  | :heavy_minus_sign:                                                                | N/A                                                                               |
| `expand`                                                                          | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `limit`                                                                           | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `offset`                                                                          | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `order`                                                                           | [Optional[models.TypesWalletFilterOrder]](../../models/typeswalletfilterorder.md) | :heavy_minus_sign:                                                                | N/A                                                                               |
| `sort`                                                                            | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `status`                                                                          | [Optional[models.TypesWalletStatus]](../../models/typeswalletstatus.md)           | :heavy_minus_sign:                                                                | N/A                                                                               |
| `wallet_ids`                                                                      | List[*str*]                                                                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.TypesListResponseDtoWalletResponse](../../models/typeslistresponsedtowalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## query_wallet_transaction

Use when searching or reporting on wallet transactions (e.g. cross-wallet history or reconciliation). Returns a paginated list; supports filtering by wallet, customer, type, date range.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryWalletTransaction" method="post" path="/wallets/transactions/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.query_wallet_transaction()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `created_by`                                                                                            | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `credits_available_gt`                                                                                  | *Optional[float]*                                                                                       | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `end_time`                                                                                              | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `expand`                                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `expiry_date_after`                                                                                     | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `expiry_date_before`                                                                                    | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `filters`                                                                                               | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]                               | :heavy_minus_sign:                                                                                      | filters allows complex filtering based on multiple fields                                               |
| `id`                                                                                                    | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `limit`                                                                                                 | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `offset`                                                                                                | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `order`                                                                                                 | [Optional[models.TypesWalletTransactionFilterOrder]](../../models/typeswallettransactionfilterorder.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `priority`                                                                                              | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `reference_id`                                                                                          | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `reference_type`                                                                                        | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `sort`                                                                                                  | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                                   | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `start_time`                                                                                            | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `status`                                                                                                | [Optional[models.TypesStatus]](../../models/typesstatus.md)                                             | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `transaction_reason`                                                                                    | [Optional[models.TypesTransactionReason]](../../models/typestransactionreason.md)                       | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `transaction_status`                                                                                    | [Optional[models.TypesTransactionStatus]](../../models/typestransactionstatus.md)                       | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `type`                                                                                                  | [Optional[models.TypesTransactionType]](../../models/typestransactiontype.md)                           | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |

### Response

**[models.DtoListWalletTransactionsResponse](../../models/dtolistwallettransactionsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_wallet

Use when you need to load a single wallet (e.g. for a balance or settings view).

### Example Usage

<!-- UsageSnippet language="python" operationID="getWallet" method="get" path="/wallets/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.get_wallet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Wallet ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoWalletResponse](../../models/dtowalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_wallet

Use when changing wallet settings (e.g. enabling or updating auto top-up thresholds).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateWallet" method="put" path="/wallets/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.update_wallet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `id`                                                                      | *str*                                                                     | :heavy_check_mark:                                                        | Wallet ID                                                                 |
| `alert_settings`                                                          | [Optional[models.TypesAlertSettings]](../../models/typesalertsettings.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `auto_topup`                                                              | [Optional[models.TypesAutoTopup]](../../models/typesautotopup.md)         | :heavy_minus_sign:                                                        | N/A                                                                       |
| `config`                                                                  | [Optional[models.TypesWalletConfig]](../../models/typeswalletconfig.md)   | :heavy_minus_sign:                                                        | N/A                                                                       |
| `description`                                                             | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `metadata`                                                                | Dict[str, *str*]                                                          | :heavy_minus_sign:                                                        | N/A                                                                       |
| `name`                                                                    | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.DtoWalletResponse](../../models/dtowalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_wallet_balance

Use when displaying or checking current wallet balance (e.g. before charging or in a portal). Supports optional expand for credits breakdown and from_cache.

### Example Usage

<!-- UsageSnippet language="python" operationID="getWalletBalance" method="get" path="/wallets/{id}/balance/real-time" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.get_wallet_balance(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Wallet ID                                                           |
| `expand`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Expand fields (e.g., credits_available_breakdown)                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoWalletBalanceResponse](../../models/dtowalletbalanceresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## terminate_wallet

Use when closing a customer wallet (e.g. churn or migration). Closes the wallet and applies remaining balance per policy (refund or forfeit).

### Example Usage

<!-- UsageSnippet language="python" operationID="terminateWallet" method="post" path="/wallets/{id}/terminate" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.terminate_wallet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Wallet ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoWalletResponse](../../models/dtowalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## top_up_wallet

Use when adding funds to a wallet (e.g. top-up, refund, or manual credit). Supports optional idempotency via reference.

### Example Usage

<!-- UsageSnippet language="python" operationID="topUpWallet" method="post" path="/wallets/{id}/top-up" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.top_up_wallet(id="<id>", transaction_reason="MANUAL_BALANCE_DEBIT")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                       | Wallet ID                                                                                                                                                                                                                                                                                                                                                                                |
| `transaction_reason`                                                                                                                                                                                                                                                                                                                                                                     | [models.TypesTransactionReason](../../models/typestransactionreason.md)                                                                                                                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                                                                                                                                      |
| `amount`                                                                                                                                                                                                                                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | amount is the amount in the currency of the wallet to be added<br/>NOTE: this is not the number of credits to add, but the amount in the currency<br/>amount = credits_to_add * conversion_rate<br/>if both amount and credits_to_add are provided, amount will be ignored<br/>ex if the wallet has a conversion_rate of 2 then adding an amount of<br/>10 USD in the wallet wil add 5 credits in the wallet |
| `credits_to_add`                                                                                                                                                                                                                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | credits_to_add is the number of credits to add to the wallet                                                                                                                                                                                                                                                                                                                             |
| `description`                                                                                                                                                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | description to add any specific details about the transaction                                                                                                                                                                                                                                                                                                                            |
| `expiry_date_utc`                                                                                                                                                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | expiry_date_utc is the expiry date in UTC timezone<br/>ex 2025-01-01 00:00:00 UTC                                                                                                                                                                                                                                                                                                        |
| `idempotency_key`                                                                                                                                                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | idempotency_key is a unique key for the transaction                                                                                                                                                                                                                                                                                                                                      |
| `metadata`                                                                                                                                                                                                                                                                                                                                                                               | Dict[str, *str*]                                                                                                                                                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                                                                                                                                      |
| `priority`                                                                                                                                                                                                                                                                                                                                                                               | *Optional[int]*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | priority is the priority of the transaction<br/>lower number means higher priority<br/>default is nil which means no priority at all                                                                                                                                                                                                                                                     |
| `retries`                                                                                                                                                                                                                                                                                                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                       | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                                      |

### Response

**[models.DtoTopUpWalletResponse](../../models/dtotopupwalletresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_wallet_transactions

Use when showing transaction history for a wallet (e.g. credit/debit log or audit). Returns a paginated list; supports limit, offset, and filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getWalletTransactions" method="get" path="/wallets/{id}/transactions" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.wallets.get_wallet_transactions(id_path_parameter="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `id_path_parameter`                                                                         | *str*                                                                                       | :heavy_check_mark:                                                                          | Wallet ID                                                                                   |
| `created_by`                                                                                | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `credits_available_gt`                                                                      | *Optional[float]*                                                                           | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `end_time`                                                                                  | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `expand`                                                                                    | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `expiry_date_after`                                                                         | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `expiry_date_before`                                                                        | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `id_query_parameter`                                                                        | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `limit`                                                                                     | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `offset`                                                                                    | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `order`                                                                                     | [Optional[models.GetWalletTransactionsOrder]](../../models/getwallettransactionsorder.md)   | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `priority`                                                                                  | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `reference_id`                                                                              | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `reference_type`                                                                            | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `start_time`                                                                                | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `status`                                                                                    | [Optional[models.GetWalletTransactionsStatus]](../../models/getwallettransactionsstatus.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `transaction_reason`                                                                        | [Optional[models.TransactionReason]](../../models/transactionreason.md)                     | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `transaction_status`                                                                        | [Optional[models.TransactionStatus]](../../models/transactionstatus.md)                     | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `type`                                                                                      | [Optional[models.Type]](../../models/type.md)                                               | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.DtoListWalletTransactionsResponse](../../models/dtolistwallettransactionsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |