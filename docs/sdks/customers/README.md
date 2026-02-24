# Customers

## Overview

### Available Operations

* [update_customer](#update_customer) - Update customer
* [create_customer](#create_customer) - Create customer
* [get_customer_by_external_id](#get_customer_by_external_id) - Get customer by external ID
* [query_customer](#query_customer) - Query customers
* [get_customer_usage_summary](#get_customer_usage_summary) - Get customer usage summary
* [get_customer](#get_customer) - Get customer
* [delete_customer](#delete_customer) - Delete customer
* [get_customer_entitlements](#get_customer_entitlements) - Get customer entitlements
* [get_customer_upcoming_grants](#get_customer_upcoming_grants) - Get upcoming credit grant applications

## update_customer

Use when updating customer details (e.g. name, email, or metadata). Identify by id or external_customer_id.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCustomer" method="put" path="/customers" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.update_customer()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                         | Type                                                                                                                                                                                                                                              | Required                                                                                                                                                                                                                                          | Description                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                                                                                                                                                              | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | Customer ID                                                                                                                                                                                                                                       |
| `external_customer_id`                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | Customer External ID                                                                                                                                                                                                                              |
| `address_city`                                                                                                                                                                                                                                    | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_city is the updated city name with maximum 100 characters                                                                                                                                                                                 |
| `address_country`                                                                                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_country is the updated two-letter ISO 3166-1 alpha-2 country code                                                                                                                                                                         |
| `address_line1`                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_line1 is the updated primary address line with maximum 255 characters                                                                                                                                                                     |
| `address_line2`                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_line2 is the updated secondary address line with maximum 255 characters                                                                                                                                                                   |
| `address_postal_code`                                                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_postal_code is the updated postal code with maximum 20 characters                                                                                                                                                                         |
| `address_state`                                                                                                                                                                                                                                   | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | address_state is the updated state, province, or region name with maximum 100 characters                                                                                                                                                          |
| `email`                                                                                                                                                                                                                                           | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | email is the updated email address and must be a valid email format if provided                                                                                                                                                                   |
| `external_id`                                                                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | external_id is the updated external identifier for the customer                                                                                                                                                                                   |
| `integration_entity_mapping`                                                                                                                                                                                                                      | List[[models.DtoIntegrationEntityMapping](../../models/dtointegrationentitymapping.md)]                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                | integration_entity_mapping contains provider integration mappings for this customer                                                                                                                                                               |
| `metadata`                                                                                                                                                                                                                                        | Dict[str, *str*]                                                                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                | metadata contains updated key-value pairs that will replace existing metadata                                                                                                                                                                     |
| `name`                                                                                                                                                                                                                                            | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | name is the updated name or company name for the customer                                                                                                                                                                                         |
| `parent_customer_external_id`                                                                                                                                                                                                                     | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | parent_customer_external_id is the external ID of the parent customer from your system<br/>Exactly one of parent_customer_id or parent_customer_external_id may be provided<br/>If you provide the external ID, the parent customer value will be ignored |
| `parent_customer_id`                                                                                                                                                                                                                              | *Optional[str]*                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                | parent_customer_id is the internal FlexPrice ID of the parent customer                                                                                                                                                                            |
| `retries`                                                                                                                                                                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                | Configuration to override the default retry behavior of the client.                                                                                                                                                                               |

### Response

**[models.DtoCustomerResponse](../../models/dtocustomerresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_customer

Use when onboarding a new billing customer (e.g. sign-up or CRM sync). Ideal for linking via external_customer_id to your app's user id.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCustomer" method="post" path="/customers" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.create_customer(external_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                     | Type                                                                                                                                                                                                          | Required                                                                                                                                                                                                      | Description                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `external_id`                                                                                                                                                                                                 | *str*                                                                                                                                                                                                         | :heavy_check_mark:                                                                                                                                                                                            | external_id is the unique identifier from your system to reference this customer (required)                                                                                                                   |
| `address_city`                                                                                                                                                                                                | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_city is the city name with maximum 100 characters                                                                                                                                                     |
| `address_country`                                                                                                                                                                                             | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_country is the two-letter ISO 3166-1 alpha-2 country code                                                                                                                                             |
| `address_line1`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_line1 is the primary address line with maximum 255 characters                                                                                                                                         |
| `address_line2`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_line2 is the secondary address line with maximum 255 characters                                                                                                                                       |
| `address_postal_code`                                                                                                                                                                                         | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_postal_code is the ZIP code or postal code with maximum 20 characters                                                                                                                                 |
| `address_state`                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | address_state is the state, province, or region name with maximum 100 characters                                                                                                                              |
| `email`                                                                                                                                                                                                       | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | email is the customer's email address and must be a valid email format if provided                                                                                                                            |
| `integration_entity_mapping`                                                                                                                                                                                  | List[[models.DtoIntegrationEntityMapping](../../models/dtointegrationentitymapping.md)]                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                            | integration_entity_mapping contains provider integration mappings for this customer                                                                                                                           |
| `metadata`                                                                                                                                                                                                    | Dict[str, *str*]                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | metadata contains additional key-value pairs for storing extra information                                                                                                                                    |
| `name`                                                                                                                                                                                                        | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | name is the full name or company name of the customer                                                                                                                                                         |
| `parent_customer_external_id`                                                                                                                                                                                 | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | parent_customer_external_id is the external ID of the parent customer from your system<br/>Exactly one of parent_customer_id or parent_customer_external_id may be provided                                   |
| `parent_customer_id`                                                                                                                                                                                          | *Optional[str]*                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                            | parent_customer_id is the internal FlexPrice ID of the parent customer                                                                                                                                        |
| `skip_onboarding_workflow`                                                                                                                                                                                    | *Optional[bool]*                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | skip_onboarding_workflow when true, prevents the customer onboarding workflow from being triggered<br/>This is used internally when a customer is created via a workflow to prevent infinite loops<br/>Default: false |
| `tax_rate_overrides`                                                                                                                                                                                          | List[[models.DtoTaxRateOverride](../../models/dtotaxrateoverride.md)]                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                            | tax_rate_overrides contains tax rate configurations to be linked to this customer                                                                                                                             |
| `retries`                                                                                                                                                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                            | Configuration to override the default retry behavior of the client.                                                                                                                                           |

### Response

**[models.DtoCustomerResponse](../../models/dtocustomerresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_customer_by_external_id

Use when resolving a customer by your app's id (e.g. from your user table). Ideal for integrations that key by external id.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerByExternalId" method="get" path="/customers/external/{external_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.get_customer_by_external_id(external_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `external_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Customer External ID                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCustomerResponse](../../models/dtocustomerresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_customer

Use when listing or searching customers (e.g. admin CRM or reporting). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryCustomer" method="post" path="/customers/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.query_customer()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `customer_ids`                                                                        | List[*str*]                                                                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `email`                                                                               | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `end_time`                                                                            | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `expand`                                                                              | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `external_id`                                                                         | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `external_ids`                                                                        | List[*str*]                                                                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `filters`                                                                             | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]             | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `limit`                                                                               | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `offset`                                                                              | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `order`                                                                               | [Optional[models.TypesCustomerFilterOrder]](../../models/typescustomerfilterorder.md) | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `parent_customer_ids`                                                                 | List[*str*]                                                                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `sort`                                                                                | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                 | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `start_time`                                                                          | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `status`                                                                              | [Optional[models.TypesStatus]](../../models/typesstatus.md)                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `retries`                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                      | :heavy_minus_sign:                                                                    | Configuration to override the default retry behavior of the client.                   |

### Response

**[models.DtoListCustomersResponse](../../models/dtolistcustomersresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_customer_usage_summary

Use when showing a customer's usage (e.g. portal or overage alerts). Identify by customer_id or customer_lookup_key; supports filters.

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerUsageSummary" method="get" path="/customers/usage" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.get_customer_usage_summary()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `customer_id`                                                       | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `customer_lookup_key`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `feature_ids`                                                       | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `feature_lookup_keys`                                               | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `subscription_ids`                                                  | List[*str*]                                                         | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCustomerUsageSummaryResponse](../../models/dtocustomerusagesummaryresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_customer

Use when you need to load a single customer (e.g. for a billing portal or to attach a subscription).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomer" method="get" path="/customers/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.get_customer(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCustomerResponse](../../models/dtocustomerresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_customer

Use when removing a customer (e.g. GDPR or churn). Returns 204 No Content on success.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCustomer" method="delete" path="/customers/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    sdk.customers.delete_customer(id="<id>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_customer_entitlements

Use when checking what a customer can access (e.g. feature gating or usage limits). Supports optional filters (feature_ids, subscription_ids).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerEntitlements" method="get" path="/customers/{id}/entitlements" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.get_customer_entitlements(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCustomerEntitlementsResponse](../../models/dtocustomerentitlementsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_customer_upcoming_grants

Use when showing upcoming or pending credits for a customer (e.g. in a portal or for forecasting).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCustomerUpcomingGrants" method="get" path="/customers/{id}/grants/upcoming" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.customers.get_customer_upcoming_grants(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Customer ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListCreditGrantApplicationsResponse](../../models/dtolistcreditgrantapplicationsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |