# Costs

## Overview

### Available Operations

* [create_costsheet](#create_costsheet) - Create costsheet
* [get_active_costsheet](#get_active_costsheet) - Get active costsheet
* [get_detailed_cost_analytics](#get_detailed_cost_analytics) - Get combined revenue and cost analytics
* [get_detailed_cost_analytics_v2](#get_detailed_cost_analytics_v2) - Get combined revenue and cost analytics (V2)
* [query_costsheet](#query_costsheet) - Query costsheets
* [get_costsheet](#get_costsheet) - Get costsheet
* [update_costsheet](#update_costsheet) - Update costsheet
* [delete_costsheet](#delete_costsheet) - Delete costsheet

## create_costsheet

Use when setting up a new pricing configuration (e.g. a new product or region). Costsheets group prices and define the default for the environment.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCostsheet" method="post" path="/costs" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.create_costsheet(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `lookup_key`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreateCostsheetResponse](../../models/dtocreatecostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 409                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_active_costsheet

Use when you need the tenant's default pricing configuration (e.g. for checkout or plan display). Returns the active costsheet for the environment.

### Example Usage

<!-- UsageSnippet language="python" operationID="getActiveCostsheet" method="get" path="/costs/active" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.get_active_costsheet()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCostsheetResponse](../../models/dtocostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 404                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_detailed_cost_analytics

Use when building dashboards or reports that need revenue vs cost, ROI, and margin over a time period (e.g. finance views or executive summaries).

### Example Usage

<!-- UsageSnippet language="python" operationID="getDetailedCostAnalytics" method="post" path="/costs/analytics" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.get_detailed_cost_analytics()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                              | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `end_time`                                                             | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | N/A                                                                    |
| `expand`                                                               | List[*str*]                                                            | :heavy_minus_sign:                                                     | Expand options - specify which entities to expand                      |
| `external_customer_id`                                                 | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | Optional - for specific customer                                       |
| `feature_ids`                                                          | List[*str*]                                                            | :heavy_minus_sign:                                                     | Additional filters                                                     |
| `limit`                                                                | *Optional[int]*                                                        | :heavy_minus_sign:                                                     | Pagination                                                             |
| `offset`                                                               | *Optional[int]*                                                        | :heavy_minus_sign:                                                     | N/A                                                                    |
| `start_time`                                                           | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | Time range fields (optional - defaults to last 7 days if not provided) |
| `retries`                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)       | :heavy_minus_sign:                                                     | Configuration to override the default retry behavior of the client.    |

### Response

**[models.DtoGetDetailedCostAnalyticsResponse](../../models/dtogetdetailedcostanalyticsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_detailed_cost_analytics_v2

Use when you need the same revenue/cost/ROI analytics but computed from the costsheet usage-tracking pipeline (e.g. for consistency with usage-based cost data).

### Example Usage

<!-- UsageSnippet language="python" operationID="getDetailedCostAnalyticsV2" method="post" path="/costs/analytics-v2" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.get_detailed_cost_analytics_v2()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                              | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `end_time`                                                             | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | N/A                                                                    |
| `expand`                                                               | List[*str*]                                                            | :heavy_minus_sign:                                                     | Expand options - specify which entities to expand                      |
| `external_customer_id`                                                 | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | Optional - for specific customer                                       |
| `feature_ids`                                                          | List[*str*]                                                            | :heavy_minus_sign:                                                     | Additional filters                                                     |
| `limit`                                                                | *Optional[int]*                                                        | :heavy_minus_sign:                                                     | Pagination                                                             |
| `offset`                                                               | *Optional[int]*                                                        | :heavy_minus_sign:                                                     | N/A                                                                    |
| `start_time`                                                           | *Optional[str]*                                                        | :heavy_minus_sign:                                                     | Time range fields (optional - defaults to last 7 days if not provided) |
| `retries`                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)       | :heavy_minus_sign:                                                     | Configuration to override the default retry behavior of the client.    |

### Response

**[models.DtoGetDetailedCostAnalyticsResponse](../../models/dtogetdetailedcostanalyticsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_costsheet

Use when listing or searching costsheets (e.g. admin catalog). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryCostsheet" method="post" path="/costs/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.query_costsheet()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `costsheet_i_ds`                                                              | List[*str*]                                                                   | :heavy_minus_sign:                                                            | CostsheetIDs allows filtering by specific costsheet IDs                       |
| `environment_id`                                                              | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | EnvironmentID filters by specific environment ID                              |
| `filters`                                                                     | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]     | :heavy_minus_sign:                                                            | Filters contains custom filtering conditions                                  |
| `lookup_key`                                                                  | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | LookupKey filters by lookup key                                               |
| `name`                                                                        | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | Name filters by costsheet name                                                |
| `query_filter`                                                                | [Optional[models.TypesQueryFilter]](../../models/typesqueryfilter.md)         | :heavy_minus_sign:                                                            | N/A                                                                           |
| `sort`                                                                        | List[[models.TypesSortCondition](../../models/typessortcondition.md)]         | :heavy_minus_sign:                                                            | Sort specifies result ordering preferences                                    |
| `status`                                                                      | [Optional[models.TypesStatus]](../../models/typesstatus.md)                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `tenant_id`                                                                   | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | TenantID filters by specific tenant ID                                        |
| `time_range_filter`                                                           | [Optional[models.TypesTimeRangeFilter]](../../models/typestimerangefilter.md) | :heavy_minus_sign:                                                            | N/A                                                                           |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.DtoListCostsheetResponse](../../models/dtolistcostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_costsheet

Use when you need to load a single costsheet (e.g. for editing or display). Supports optional expand for related prices.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCostsheet" method="get" path="/costs/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.get_costsheet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Costsheet ID                                                        |
| `expand`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Comma-separated list of fields to expand (e.g., 'prices')           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoGetCostsheetResponse](../../models/dtogetcostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_costsheet

Use when changing costsheet name or metadata.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCostsheet" method="put" path="/costs/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.update_costsheet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Costsheet ID                                                        |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `lookup_key`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoUpdateCostsheetResponse](../../models/dtoupdatecostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404, 409              | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_costsheet

Use when retiring a costsheet (e.g. end-of-life product). Soft-deletes; status set to deleted.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCostsheet" method="delete" path="/costs/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.costs.delete_costsheet(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Costsheet ID                                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoDeleteCostsheetResponse](../../models/dtodeletecostsheetresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |