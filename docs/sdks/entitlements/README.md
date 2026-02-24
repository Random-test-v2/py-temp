# Entitlements

## Overview

### Available Operations

* [get_addon_entitlements](#get_addon_entitlements) - Get addon entitlements
* [create_entitlement](#create_entitlement) - Create entitlement
* [create_entitlements_bulk](#create_entitlements_bulk) - Create entitlements in bulk
* [query_entitlement](#query_entitlement) - Query entitlements
* [get_entitlement](#get_entitlement) - Get entitlement
* [update_entitlement](#update_entitlement) - Update entitlement
* [delete_entitlement](#delete_entitlement) - Delete entitlement
* [get_plan_entitlements](#get_plan_entitlements) - Get plan entitlements

## get_addon_entitlements

Use when checking what features or limits an addon grants (e.g. for display or entitlement logic).

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddonEntitlements" method="get" path="/addons/{id}/entitlements" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.get_addon_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListEntitlementsResponse](../../models/dtolistentitlementsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_entitlement

Use when attaching a feature (and its limit) to a plan or addon (e.g. "10 seats" or "1000 API calls"). Defines what the plan/addon includes.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntitlement" method="post" path="/entitlements" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.create_entitlement(feature_id="<id>", feature_type="metered")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `feature_id`                                                                                          | *str*                                                                                                 | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `feature_type`                                                                                        | [models.TypesFeatureType](../../models/typesfeaturetype.md)                                           | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `end_date`                                                                                            | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `entity_id`                                                                                           | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `entity_type`                                                                                         | [Optional[models.TypesEntitlementEntityType]](../../models/typesentitlemententitytype.md)             | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `is_enabled`                                                                                          | *Optional[bool]*                                                                                      | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `is_soft_limit`                                                                                       | *Optional[bool]*                                                                                      | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `parent_entitlement_id`                                                                               | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `plan_id`                                                                                             | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `start_date`                                                                                          | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `static_value`                                                                                        | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `usage_limit`                                                                                         | *Optional[int]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `usage_reset_period`                                                                                  | [Optional[models.TypesEntitlementUsageResetPeriod]](../../models/typesentitlementusageresetperiod.md) | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `retries`                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                      | :heavy_minus_sign:                                                                                    | Configuration to override the default retry behavior of the client.                                   |

### Response

**[models.DtoEntitlementResponse](../../models/dtoentitlementresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_entitlements_bulk

Use when attaching many features to a plan or addon at once (e.g. initial plan setup or import). Bulk version of create entitlement.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntitlementsBulk" method="post" path="/entitlements/bulk" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.create_entitlements_bulk(items=[
        {
            "feature_id": "<id>",
            "feature_type": "static",
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `items`                                                                                 | List[[models.DtoCreateEntitlementRequest](../../models/dtocreateentitlementrequest.md)] | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.DtoCreateBulkEntitlementResponse](../../models/dtocreatebulkentitlementresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_entitlement

Use when listing or searching entitlements (e.g. plan editor or audit). Returns a paginated list; supports filtering by plan, addon, feature.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryEntitlement" method="post" path="/entitlements/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.query_entitlement()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `end_time`                                                                                  | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `entity_ids`                                                                                | List[*str*]                                                                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `entity_type`                                                                               | [Optional[models.TypesEntitlementEntityType]](../../models/typesentitlemententitytype.md)   | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `expand`                                                                                    | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `feature_ids`                                                                               | List[*str*]                                                                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `feature_type`                                                                              | [Optional[models.TypesFeatureType]](../../models/typesfeaturetype.md)                       | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `filters`                                                                                   | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]                   | :heavy_minus_sign:                                                                          | Specific filters for entitlements                                                           |
| `is_enabled`                                                                                | *Optional[bool]*                                                                            | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `limit`                                                                                     | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `offset`                                                                                    | *Optional[int]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `order`                                                                                     | [Optional[models.TypesEntitlementFilterOrder]](../../models/typesentitlementfilterorder.md) | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `plan_ids`                                                                                  | List[*str*]                                                                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `sort`                                                                                      | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                       | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `start_time`                                                                                | *Optional[str]*                                                                             | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `status`                                                                                    | [Optional[models.TypesStatus]](../../models/typesstatus.md)                                 | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.DtoListEntitlementsResponse](../../models/dtolistentitlementsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_entitlement

Use when you need to load a single entitlement (e.g. to display or edit a feature limit).

### Example Usage

<!-- UsageSnippet language="python" operationID="getEntitlement" method="get" path="/entitlements/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.get_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Entitlement ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoEntitlementResponse](../../models/dtoentitlementresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_entitlement

Use when changing an entitlement (e.g. increasing or decreasing a limit). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateEntitlement" method="put" path="/entitlements/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.update_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `id`                                                                                                  | *str*                                                                                                 | :heavy_check_mark:                                                                                    | Entitlement ID                                                                                        |
| `is_enabled`                                                                                          | *Optional[bool]*                                                                                      | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `is_soft_limit`                                                                                       | *Optional[bool]*                                                                                      | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `static_value`                                                                                        | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `usage_limit`                                                                                         | *Optional[int]*                                                                                       | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `usage_reset_period`                                                                                  | [Optional[models.TypesEntitlementUsageResetPeriod]](../../models/typesentitlementusageresetperiod.md) | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `retries`                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                      | :heavy_minus_sign:                                                                                    | Configuration to override the default retry behavior of the client.                                   |

### Response

**[models.DtoEntitlementResponse](../../models/dtoentitlementresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_entitlement

Use when removing a feature from a plan or addon (e.g. deprecating a capability). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteEntitlement" method="delete" path="/entitlements/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.delete_entitlement(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Entitlement ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_plan_entitlements

Use when checking what a plan includes (e.g. feature list or limits for display or gating).

### Example Usage

<!-- UsageSnippet language="python" operationID="getPlanEntitlements" method="get" path="/plans/{id}/entitlements" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entitlements.get_plan_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Plan ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoPlanResponse](../../models/dtoplanresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |