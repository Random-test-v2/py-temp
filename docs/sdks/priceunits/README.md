# PriceUnits

## Overview

### Available Operations

* [list_price_units](#list_price_units) - List price units
* [create_price_unit](#create_price_unit) - Create price unit
* [get_price_unit_by_code](#get_price_unit_by_code) - Get price unit by code
* [query_price_unit](#query_price_unit) - Query price units
* [get_price_unit](#get_price_unit) - Get price unit
* [update_price_unit](#update_price_unit) - Update price unit
* [delete_price_unit](#delete_price_unit) - Delete price unit

## list_price_units

Use when listing price units (e.g. in a catalog or when creating prices). Returns a paginated list; supports status, sort, and pagination.

### Example Usage

<!-- UsageSnippet language="python" operationID="listPriceUnits" method="get" path="/prices/units" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.list_price_units(limit=50, offset=0)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `status`                                                                    | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | Filter by status                                                            |
| `limit`                                                                     | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | Limit number of results                                                     |
| `offset`                                                                    | *Optional[int]*                                                             | :heavy_minus_sign:                                                          | Offset for pagination                                                       |
| `sort`                                                                      | *Optional[str]*                                                             | :heavy_minus_sign:                                                          | Sort field                                                                  |
| `order`                                                                     | [Optional[models.ListPriceUnitsOrder]](../../models/listpriceunitsorder.md) | :heavy_minus_sign:                                                          | Sort order                                                                  |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |

### Response

**[models.DtoListPriceUnitsResponse](../../models/dtolistpriceunitsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## create_price_unit

Use when defining a new unit of measure for pricing (e.g. GB, API call, seat). Ideal for metered or usage-based prices.

### Example Usage

<!-- UsageSnippet language="python" operationID="createPriceUnit" method="post" path="/prices/units" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.create_price_unit(base_currency="<value>", code="<value>", conversion_rate="<value>", name="<value>", symbol="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `base_currency`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | *str*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | base_currency  is the currency that the price unit is based on                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `code`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `conversion_rate`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | *str*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | ConversionRate defines the exchange rate from this price unit to the base currency.<br/>This rate is used to convert amounts in the custom price unit to the base currency for storage and billing.<br/><br/>Conversion formula:<br/>  price_unit_amount * conversion_rate = base_currency_amount<br/><br/>Example:<br/>  If conversion_rate = "0.01" and base_currency = "usd":<br/>  100 price_unit tokens * 0.01 = 1.00 USD<br/><br/>Note: Rounding precision is determined by the base currency (e.g., USD uses 2 decimal places, JPY uses 0). |
| `name`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `symbol`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | *str*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `metadata`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Dict[str, *str*]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `retries`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                                                                                                                                                                                                                                        |

### Response

**[models.DtoCreatePriceUnitResponse](../../models/dtocreatepriceunitresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_price_unit_by_code

Use when resolving a price unit by code (e.g. from an external catalog or config). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="python" operationID="getPriceUnitByCode" method="get" path="/prices/units/code/{code}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.get_price_unit_by_code(code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `code`                                                              | *str*                                                               | :heavy_check_mark:                                                  | Price unit code                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPriceUnitResponse](../../models/dtopriceunitresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## query_price_unit

Use when searching or listing price units (e.g. admin catalog). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryPriceUnit" method="post" path="/prices/units/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.query_price_unit()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `end_time`                                                                              | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `expand`                                                                                | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `filters`                                                                               | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]               | :heavy_minus_sign:                                                                      | filters allows complex filtering based on multiple fields                               |
| `limit`                                                                                 | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `offset`                                                                                | *Optional[int]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `order`                                                                                 | [Optional[models.TypesPriceUnitFilterOrder]](../../models/typespriceunitfilterorder.md) | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `price_unit_ids`                                                                        | List[*str*]                                                                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `sort`                                                                                  | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                   | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `start_time`                                                                            | *Optional[str]*                                                                         | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `status`                                                                                | [Optional[models.TypesStatus]](../../models/typesstatus.md)                             | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.DtoListPriceUnitsResponse](../../models/dtolistpriceunitsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_price_unit

Use when you need to load a single price unit (e.g. for display or when creating a price).

### Example Usage

<!-- UsageSnippet language="python" operationID="getPriceUnit" method="get" path="/prices/units/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.get_price_unit(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Price unit ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPriceUnitResponse](../../models/dtopriceunitresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_price_unit

Use when renaming or updating metadata for a price unit. Code is immutable once created.

### Example Usage

<!-- UsageSnippet language="python" operationID="updatePriceUnit" method="put" path="/prices/units/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.update_price_unit(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Price unit ID                                                       |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPriceUnitResponse](../../models/dtopriceunitresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_price_unit

Use when removing a price unit that is no longer needed. Fails if any price references this unit.

### Example Usage

<!-- UsageSnippet language="python" operationID="deletePriceUnit" method="delete" path="/prices/units/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.price_units.delete_price_unit(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Price unit ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |