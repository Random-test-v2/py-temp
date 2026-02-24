# Addons

## Overview

### Available Operations

* [create_addon](#create_addon) - Create addon
* [get_addon_by_lookup_key](#get_addon_by_lookup_key) - Get addon by lookup key
* [query_addon](#query_addon) - Query addons
* [get_addon](#get_addon) - Get addon
* [update_addon](#update_addon) - Update addon
* [delete_addon](#delete_addon) - Delete addon

## create_addon

Use when defining an optional purchasable item (e.g. extra storage or support tier). Ideal for add-ons that customers can attach to a subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="createAddon" method="post" path="/addons" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `type`                                                              | [models.TypesAddonType](../../models/typesaddontype.md)             | :heavy_check_mark:                                                  | N/A                                                                 |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreateAddonResponse](../../models/dtocreateaddonresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_addon_by_lookup_key

Use when resolving an addon by external id (e.g. from your product catalog). Ideal for integrations.

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddonByLookupKey" method="get" path="/addons/lookup/{lookup_key}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.get_addon_by_lookup_key(lookup_key="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `lookup_key`                                                        | *str*                                                               | :heavy_check_mark:                                                  | Addon Lookup Key                                                    |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoAddonResponse](../../models/dtoaddonresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## query_addon

Use when listing or searching addons (e.g. catalog or subscription builder). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAddon" method="post" path="/addons/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.query_addon()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `addon_ids`                                                                     | List[*str*]                                                                     | :heavy_minus_sign:                                                              | N/A                                                                             |
| `addon_type`                                                                    | [Optional[models.TypesAddonType]](../../models/typesaddontype.md)               | :heavy_minus_sign:                                                              | N/A                                                                             |
| `end_time`                                                                      | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `expand`                                                                        | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `filters`                                                                       | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]       | :heavy_minus_sign:                                                              | filters allows complex filtering based on multiple fields                       |
| `limit`                                                                         | *Optional[int]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `lookup_keys`                                                                   | List[*str*]                                                                     | :heavy_minus_sign:                                                              | N/A                                                                             |
| `offset`                                                                        | *Optional[int]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `order`                                                                         | [Optional[models.TypesAddonFilterOrder]](../../models/typesaddonfilterorder.md) | :heavy_minus_sign:                                                              | N/A                                                                             |
| `sort`                                                                          | List[[models.TypesSortCondition](../../models/typessortcondition.md)]           | :heavy_minus_sign:                                                              | N/A                                                                             |
| `start_time`                                                                    | *Optional[str]*                                                                 | :heavy_minus_sign:                                                              | N/A                                                                             |
| `status`                                                                        | [Optional[models.TypesStatus]](../../models/typesstatus.md)                     | :heavy_minus_sign:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.DtoListAddonsResponse](../../models/dtolistaddonsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_addon

Use when you need to load a single addon (e.g. for display or to attach to a subscription).

### Example Usage

<!-- UsageSnippet language="python" operationID="getAddon" method="get" path="/addons/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.get_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoAddonResponse](../../models/dtoaddonresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_addon

Use when changing addon details (e.g. name, pricing, or metadata).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateAddon" method="put" path="/addons/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.update_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `description`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoAddonResponse](../../models/dtoaddonresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_addon

Use when retiring an addon (e.g. end-of-life). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteAddon" method="delete" path="/addons/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.delete_addon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Addon ID                                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |