# CreditGrants

## Overview

### Available Operations

* [create_credit_grant](#create_credit_grant) - Create credit grant
* [get_credit_grant](#get_credit_grant) - Get credit grant
* [update_credit_grant](#update_credit_grant) - Update credit grant
* [delete_credit_grant](#delete_credit_grant) - Delete credit grant
* [get_plan_credit_grants](#get_plan_credit_grants) - Get plan credit grants

## create_credit_grant

Use when giving a customer or plan credits (e.g. prepaid balance or promotional credits). Scope can be plan or subscription; supports start/end dates.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCreditGrant" method="post" path="/creditgrants" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.credit_grants.create_credit_grant(cadence="ONETIME", credits="<value>", name="<value>", scope="PLAN")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cadence`                                                                                                                                                                                                                                                | [models.TypesCreditGrantCadence](../../models/typescreditgrantcadence.md)                                                                                                                                                                                | :heavy_check_mark:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `credits`                                                                                                                                                                                                                                                | *str*                                                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `name`                                                                                                                                                                                                                                                   | *str*                                                                                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `scope`                                                                                                                                                                                                                                                  | [models.TypesCreditGrantScope](../../models/typescreditgrantscope.md)                                                                                                                                                                                    | :heavy_check_mark:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `conversion_rate`                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | amount in the currency =  number of credits * conversion_rate<br/>ex if conversion_rate is 1, then 1 USD = 1 credit<br/>ex if conversion_rate is 2, then 1 USD = 0.5 credits<br/>ex if conversion_rate is 0.5, then 1 USD = 2 credits                    |
| `end_date`                                                                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `expiration_duration`                                                                                                                                                                                                                                    | *Optional[int]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `expiration_duration_unit`                                                                                                                                                                                                                               | [Optional[models.TypesCreditGrantExpiryDurationUnit]](../../models/typescreditgrantexpirydurationunit.md)                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `expiration_type`                                                                                                                                                                                                                                        | [Optional[models.TypesCreditGrantExpiryType]](../../models/typescreditgrantexpirytype.md)                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `metadata`                                                                                                                                                                                                                                               | Dict[str, *str*]                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `period`                                                                                                                                                                                                                                                 | [Optional[models.TypesCreditGrantPeriod]](../../models/typescreditgrantperiod.md)                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `period_count`                                                                                                                                                                                                                                           | *Optional[int]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `plan_id`                                                                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `priority`                                                                                                                                                                                                                                               | *Optional[int]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `start_date`                                                                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `subscription_id`                                                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                      |
| `topup_conversion_rate`                                                                                                                                                                                                                                  | *Optional[str]*                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                       | topup_conversion_rate is the conversion rate for the topup to the currency<br/>ex if topup_conversion_rate is 1, then 1 USD = 1 credit<br/>ex if topup_conversion_rate is 2, then 1 USD = 0.5 credits<br/>ex if topup_conversion_rate is 0.5, then 1 USD = 2 credits |
| `retries`                                                                                                                                                                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                       | Configuration to override the default retry behavior of the client.                                                                                                                                                                                      |

### Response

**[models.DtoCreditGrantResponse](../../models/dtocreditgrantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_credit_grant

Use when you need to load a single credit grant (e.g. for display or to check balance).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCreditGrant" method="get" path="/creditgrants/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.credit_grants.get_credit_grant(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Credit Grant ID                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreditGrantResponse](../../models/dtocreditgrantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_credit_grant

Use when changing a credit grant (e.g. amount or end date). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCreditGrant" method="put" path="/creditgrants/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.credit_grants.update_credit_grant(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Credit Grant ID                                                     |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreditGrantResponse](../../models/dtocreditgrantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_credit_grant

Use when removing or ending a credit grant (e.g. revoke promo or close prepaid). Plan-scoped grants are archived; subscription-scoped supports optional effective_date in body.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCreditGrant" method="delete" path="/creditgrants/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.credit_grants.delete_credit_grant(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `id`                                                                                             | *str*                                                                                            | :heavy_check_mark:                                                                               | Credit Grant ID                                                                                  |
| `effective_date`                                                                                 | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | EffectiveDate is optional; when set (subscription scope) the grant end date is set to this time. |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_plan_credit_grants

Use when listing credits attached to a plan (e.g. included prepaid or promo credits).

### Example Usage

<!-- UsageSnippet language="python" operationID="getPlanCreditGrants" method="get" path="/plans/{id}/creditgrants" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.credit_grants.get_plan_credit_grants(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Plan ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListCreditGrantsResponse](../../models/dtolistcreditgrantsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |