# TaxAssociations

## Overview

### Available Operations

* [list_tax_associations](#list_tax_associations) - List tax associations
* [create_tax_association](#create_tax_association) - Create Tax Association
* [get_tax_association](#get_tax_association) - Get Tax Association
* [update_tax_association](#update_tax_association) - Update tax association
* [delete_tax_association](#delete_tax_association) - Delete tax association

## list_tax_associations

Use when listing tax associations (e.g. tax config or audit). Returns list with optional filtering.

### Example Usage

<!-- UsageSnippet language="python" operationID="listTaxAssociations" method="get" path="/taxes/associations" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_associations.list_tax_associations()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `entity_type`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Entity Type                                                         |
| `entity_id`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Entity ID                                                           |
| `tax_rate_id`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Tax Rate ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListTaxAssociationsResponse](../../models/dtolisttaxassociationsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## create_tax_association

Use when linking a tax rate to an entity (e.g. customer, product, or region) so that rate applies on invoices.

### Example Usage

<!-- UsageSnippet language="python" operationID="createTaxAssociation" method="post" path="/taxes/associations" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_associations.create_tax_association(entity_id="<id>", entity_type="customer", tax_rate_code="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `entity_id`                                                             | *str*                                                                   | :heavy_check_mark:                                                      | N/A                                                                     |
| `entity_type`                                                           | [models.TypesTaxRateEntityType](../../models/typestaxrateentitytype.md) | :heavy_check_mark:                                                      | N/A                                                                     |
| `tax_rate_code`                                                         | *str*                                                                   | :heavy_check_mark:                                                      | N/A                                                                     |
| `auto_apply`                                                            | *Optional[bool]*                                                        | :heavy_minus_sign:                                                      | N/A                                                                     |
| `currency`                                                              | *Optional[str]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `metadata`                                                              | Dict[str, *str*]                                                        | :heavy_minus_sign:                                                      | N/A                                                                     |
| `priority`                                                              | *Optional[int]*                                                         | :heavy_minus_sign:                                                      | N/A                                                                     |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.DtoTaxAssociationResponse](../../models/dtotaxassociationresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_tax_association

Use when you need to load a single tax association (e.g. for display or editing).

### Example Usage

<!-- UsageSnippet language="python" operationID="getTaxAssociation" method="get" path="/taxes/associations/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_associations.get_tax_association(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tax Config ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaxAssociationResponse](../../models/dtotaxassociationresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## update_tax_association

Use when changing a tax association (e.g. switch rate or entity). Request body contains the fields to update.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTaxAssociation" method="put" path="/taxes/associations/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_associations.update_tax_association(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tax Config ID                                                       |
| `auto_apply`                                                        | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `priority`                                                          | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaxAssociationResponse](../../models/dtotaxassociationresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## delete_tax_association

Use when removing a tax association (e.g. entity no longer subject to that rate).

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteTaxAssociation" method="delete" path="/taxes/associations/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.tax_associations.delete_tax_association(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Tax Config ID                                                       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaxAssociationResponse](../../models/dtotaxassociationresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |