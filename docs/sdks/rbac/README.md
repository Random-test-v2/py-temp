# Rbac

## Overview

### Available Operations

* [list_rbac_roles](#list_rbac_roles) - List all RBAC roles
* [get_rbac_role](#get_rbac_role) - Get a specific RBAC role

## list_rbac_roles

Use when building role pickers or permission UIs. Returns all roles with permissions and descriptions.

### Example Usage

<!-- UsageSnippet language="python" operationID="listRbacRoles" method="get" path="/rbac/roles" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.rbac.list_rbac_roles()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_rbac_role

Use when you need to show or edit a single role (e.g. role detail page). Includes permissions, name, and description.

### Example Usage

<!-- UsageSnippet language="python" operationID="getRbacRole" method="get" path="/rbac/roles/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.rbac.get_rbac_role(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Role ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |