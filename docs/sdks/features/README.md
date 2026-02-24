# Features

## Overview

### Available Operations

* [create_feature](#create_feature) - Create feature
* [query_feature](#query_feature) - Query features
* [update_feature](#update_feature) - Update feature
* [delete_feature](#delete_feature) - Delete feature

## create_feature

Use when defining a new feature or capability to gate or meter (e.g. feature flags or usage-based limits). Ideal for boolean or usage features.

### Example Usage

<!-- UsageSnippet language="python" operationID="createFeature" method="post" path="/features" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.features.create_feature(name="<value>", type_="metered", meter={
        "aggregation": {},
        "event_name": "api_request",
        "name": "API Usage Meter",
        "reset_usage": "NEVER",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `name`                                                                          | *str*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `type`                                                                          | [models.TypesFeatureType](../../models/typesfeaturetype.md)                     | :heavy_check_mark:                                                              | N/A                                                                             |
| `alert_settings`                                                                | [Optional[models.TypesAlertSettings]](../../models/typesalertsettings.md)       | :heavy_minus_sign:                                                              | N/A                                                                             |
| `description`                                                                   | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `lookup_key`                                                                    | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `metadata`                                                                      | Dict[str, *str*]                                                                | :heavy_minus_sign:                                                              | N/A                                                                             |
| `meter`                                                                         | [Optional[models.DtoCreateMeterRequest]](../../models/dtocreatemeterrequest.md) | :heavy_minus_sign:                                                              | N/A                                                                             |
| `meter_id`                                                                      | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `unit_plural`                                                                   | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `unit_singular`                                                                 | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.DtoFeatureResponse](../../models/dtofeatureresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## query_feature

Use when listing or searching features (e.g. catalog or entitlement setup). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryFeature" method="post" path="/features/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.features.query_feature()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `end_time`                                                                          | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `expand`                                                                            | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `feature_ids`                                                                       | List[*str*]                                                                         | :heavy_minus_sign:                                                                  | Feature specific filters                                                            |
| `filters`                                                                           | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]           | :heavy_minus_sign:                                                                  | filters allows complex filtering based on multiple fields                           |
| `limit`                                                                             | *Optional[int]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `lookup_key`                                                                        | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `lookup_keys`                                                                       | List[*str*]                                                                         | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `meter_ids`                                                                         | List[*str*]                                                                         | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `name_contains`                                                                     | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `offset`                                                                            | *Optional[int]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `order`                                                                             | [Optional[models.TypesFeatureFilterOrder]](../../models/typesfeaturefilterorder.md) | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `sort`                                                                              | List[[models.TypesSortCondition](../../models/typessortcondition.md)]               | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `start_time`                                                                        | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `status`                                                                            | [Optional[models.TypesStatus]](../../models/typesstatus.md)                         | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.DtoListFeaturesResponse](../../models/dtolistfeaturesresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_feature

Use when changing feature definition (e.g. name, type, or meter). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateFeature" method="put" path="/features/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.features.update_feature(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `id`                                                                      | *str*                                                                     | :heavy_check_mark:                                                        | Feature ID                                                                |
| `alert_settings`                                                          | [Optional[models.TypesAlertSettings]](../../models/typesalertsettings.md) | :heavy_minus_sign:                                                        | N/A                                                                       |
| `description`                                                             | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `filters`                                                                 | List[[models.MeterFilter](../../models/meterfilter.md)]                   | :heavy_minus_sign:                                                        | N/A                                                                       |
| `metadata`                                                                | Dict[str, *str*]                                                          | :heavy_minus_sign:                                                        | N/A                                                                       |
| `name`                                                                    | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `unit_plural`                                                             | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `unit_singular`                                                           | *Optional[str]*                                                           | :heavy_minus_sign:                                                        | N/A                                                                       |
| `retries`                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)          | :heavy_minus_sign:                                                        | Configuration to override the default retry behavior of the client.       |

### Response

**[models.DtoFeatureResponse](../../models/dtofeatureresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_feature

Use when retiring a feature (e.g. deprecated capability). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteFeature" method="delete" path="/features/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.features.delete_feature(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Feature ID                                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |