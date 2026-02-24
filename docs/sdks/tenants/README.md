# Tenants

## Overview

### Available Operations

* [get_tenant_billing_usage](#get_tenant_billing_usage) - Get billing usage for the current tenant
* [create_tenant](#create_tenant) - Create a new tenant
* [update_tenant](#update_tenant) - Update a tenant
* [get_tenant](#get_tenant) - Get tenant

## get_tenant_billing_usage

Use when showing the current tenant's billing usage (e.g. admin billing page or usage caps). Returns subscription and usage for the tenant.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTenantBillingUsage" method="get" path="/tenant/billing" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tenants.get_tenant_billing_usage()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTenantBillingUsage](../../models/dtotenantbillingusage.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_tenant

Use when provisioning a new tenant (e.g. new org or workspace). Tenants are top-level isolation boundaries.

### Example Usage

<!-- UsageSnippet language="python" operationID="createTenant" method="post" path="/tenants" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tenants.create_tenant(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `name`                                                                              | *str*                                                                               | :heavy_check_mark:                                                                  | N/A                                                                                 |
| `billing_details`                                                                   | [Optional[models.DtoTenantBillingDetails]](../../models/dtotenantbillingdetails.md) | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.DtoTenantResponse](../../models/dtotenantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_tenant

Use when changing tenant details (e.g. name or billing info). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTenant" method="put" path="/tenants/update" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tenants.update_tenant()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `billing_details`                                                                   | [Optional[models.DtoTenantBillingDetails]](../../models/dtotenantbillingdetails.md) | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `metadata`                                                                          | Dict[str, *str*]                                                                    | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `name`                                                                              | *Optional[str]*                                                                     | :heavy_minus_sign:                                                                  | N/A                                                                                 |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |

### Response

**[models.DtoTenantResponse](../../models/dtotenantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_tenant

Use when you need to load a single tenant (e.g. for display or to check billing). Typically used in admin or multi-tenant contexts.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTenant" method="get" path="/tenants/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tenants.get_tenant(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTenantResponse](../../models/dtotenantresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 404                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |