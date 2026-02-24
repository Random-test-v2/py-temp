# EntityIntegrationMappings

## Overview

### Available Operations

* [create_entity_integration_mapping](#create_entity_integration_mapping) - Create entity integration mapping
* [delete_entity_integration_mapping](#delete_entity_integration_mapping) - Delete entity integration mapping

## create_entity_integration_mapping

Use when linking a FlexPrice entity to an external system (e.g. CRM or payment provider) so you can sync or reconcile by external ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="createEntityIntegrationMapping" method="post" path="/entity-integration-mappings" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.entity_integration_mappings.create_entity_integration_mapping(entity_id="<id>", entity_type="credit_note", provider_entity_id="<id>", provider_type="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `entity_id`                                                                     | *str*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `entity_type`                                                                   | [models.TypesIntegrationEntityType](../../models/typesintegrationentitytype.md) | :heavy_check_mark:                                                              | N/A                                                                             |
| `provider_entity_id`                                                            | *str*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `provider_type`                                                                 | *str*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `metadata`                                                                      | Dict[str, *Any*]                                                                | :heavy_minus_sign:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.DtoEntityIntegrationMappingResponse](../../models/dtoentityintegrationmappingresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 401, 409              | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_entity_integration_mapping

Use when unlinking a FlexPrice entity from an external system or cleaning up stale integration mappings.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteEntityIntegrationMapping" method="delete" path="/entity-integration-mappings/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    sdk.entity_integration_mappings.delete_entity_integration_mapping(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Entity integration mapping ID                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 401, 404              | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |