# TaxRates

## Overview

### Available Operations

* [get_tax_rates](#get_tax_rates) - Get tax rates
* [create_tax_rate](#create_tax_rate) - Create a tax rate
* [get_tax_rate](#get_tax_rate) - Get a tax rate
* [update_tax_rate](#update_tax_rate) - Update a tax rate
* [delete_tax_rate](#delete_tax_rate) - Delete a tax rate

## get_tax_rates

Use when listing tax rates (e.g. tax config UI). Returns tax rates with optional filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTaxRates" method="get" path="/taxes/rates" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_rates.get_tax_rates()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `end_time`                                                              | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `expand`                                                                | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `limit`                                                                 | *Optional[int]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `offset`                                                                | *Optional[int]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `order`                                                                 | [Optional[models.GetTaxRatesOrder]](../../models/gettaxratesorder.md)   | :heavy_minus_sign:                                                      | N/A                                                                     |
| `scope`                                                                 | [Optional[models.Scope]](../../models/scope.md)                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `start_time`                                                            | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `status`                                                                | [Optional[models.GetTaxRatesStatus]](../../models/gettaxratesstatus.md) | :heavy_minus_sign:                                                      | N/A                                                                     |
| `taxrate_codes`                                                         | List[*str*]                                                             | :heavy_minus_sign:                                                      | N/A                                                                     |
| `taxrate_ids`                                                           | List[*str*]                                                             | :heavy_minus_sign:                                                      | N/A                                                                     |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[List[models.DtoTaxRateResponse]](../../models/.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## create_tax_rate

Use when defining a new tax rate (e.g. VAT or sales tax) for use in invoices. Attach to customers or products via tax associations.

### Example Usage

<!-- UsageSnippet language="python" operationID="createTaxRate" method="post" path="/taxes/rates" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_rates.create_tax_rate(code="<value>", name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `code`                                                                                | *str*                                                                                 | :heavy_check_mark:                                                                    | code is the unique alphanumeric case sensitive identifier for the tax rate (required) |
| `name`                                                                                | *str*                                                                                 | :heavy_check_mark:                                                                    | name is the human-readable name for the tax rate (required)                           |
| `description`                                                                         | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | description is an optional text description providing details about the tax rate      |
| `fixed_value`                                                                         | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | fixed_value is the fixed monetary amount when tax_rate_type is "fixed"                |
| `metadata`                                                                            | Dict[str, *str*]                                                                      | :heavy_minus_sign:                                                                    | metadata contains additional key-value pairs for storing extra information            |
| `percentage_value`                                                                    | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | percentage_value is the percentage value (0-100) when tax_rate_type is "percentage"   |
| `scope`                                                                               | [Optional[models.TypesTaxRateScope]](../../models/typestaxratescope.md)               | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `tax_rate_type`                                                                       | [Optional[models.TypesTaxRateType]](../../models/typestaxratetype.md)                 | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `retries`                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                      | :heavy_minus_sign:                                                                    | Configuration to override the default retry behavior of the client.                   |

### Response

**[models.DtoTaxRateResponse](../../models/dtotaxrateresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_tax_rate

Use when you need to load a single tax rate (e.g. for display or when creating an association).

### Example Usage

<!-- UsageSnippet language="python" operationID="getTaxRate" method="get" path="/taxes/rates/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_rates.get_tax_rate(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tax rate ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaxRateResponse](../../models/dtotaxrateresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_tax_rate

Use when changing a tax rate (e.g. rate value or name). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTaxRate" method="put" path="/taxes/rates/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_rates.update_tax_rate(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `id`                                                                          | *str*                                                                         | :heavy_check_mark:                                                            | Tax rate ID                                                                   |
| `code`                                                                        | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | code is the updated unique alphanumeric identifier for the tax rate           |
| `description`                                                                 | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | description is the updated text description for the tax rate                  |
| `metadata`                                                                    | Dict[str, *str*]                                                              | :heavy_minus_sign:                                                            | metadata contains updated key-value pairs that will replace existing metadata |
| `name`                                                                        | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | name is the updated human-readable name for the tax rate                      |
| `tax_rate_status`                                                             | [Optional[models.TypesTaxRateStatus]](../../models/typestaxratestatus.md)     | :heavy_minus_sign:                                                            | N/A                                                                           |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.DtoTaxRateResponse](../../models/dtotaxrateresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_tax_rate

Use when retiring a tax rate (e.g. no longer applicable). Fails if still referenced by associations.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteTaxRate" method="delete" path="/taxes/rates/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    flexprice.tax_rates.delete_tax_rate(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tax rate ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |