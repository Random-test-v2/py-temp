# Webhooks

## Overview

### Available Operations

* [handle_chargebee_webhook](#handle_chargebee_webhook) - Handle Chargebee webhook events
* [handle_hubspot_webhook](#handle_hubspot_webhook) - Handle HubSpot webhook events
* [handle_moyasar_webhook](#handle_moyasar_webhook) - Handle Moyasar webhook events
* [handle_nomod_webhook](#handle_nomod_webhook) - Handle Nomod webhook events
* [handle_quickbooks_webhook](#handle_quickbooks_webhook) - Handle QuickBooks webhook events
* [handle_razorpay_webhook](#handle_razorpay_webhook) - Handle Razorpay webhook events
* [handle_stripe_webhook](#handle_stripe_webhook) - Handle Stripe webhook events

## handle_chargebee_webhook

Use as the Chargebee webhook endpoint URL. Receives payment and subscription events from Chargebee to sync status into FlexPrice.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleChargebeeWebhook" method="post" path="/webhooks/chargebee/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_chargebee_webhook(tenant_id="<id>", environment_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_hubspot_webhook

Use as the HubSpot webhook endpoint URL. Receives deal and customer events (e.g. deal closed won) to create or update customers in FlexPrice.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleHubspotWebhook" method="post" path="/webhooks/hubspot/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_hubspot_webhook(tenant_id="<id>", environment_id="<id>", x_hub_spot_signature_v3="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `x_hub_spot_signature_v3`                                           | *str*                                                               | :heavy_check_mark:                                                  | HubSpot webhook signature                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_moyasar_webhook

Use as the Moyasar webhook endpoint URL. Receives payment events from Moyasar to update payment status in FlexPrice.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleMoyasarWebhook" method="post" path="/webhooks/moyasar/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_moyasar_webhook(tenant_id="<id>", environment_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `x_moyasar_signature`                                               | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Moyasar webhook signature                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_nomod_webhook

Use as the Nomod webhook endpoint URL. Receives payment and invoice events from Nomod to keep FlexPrice in sync.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleNomodWebhook" method="post" path="/webhooks/nomod/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_nomod_webhook(tenant_id="<id>", environment_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `x_api_key`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Nomod webhook secret (if configured)                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_quickbooks_webhook

Use as the QuickBooks webhook endpoint URL. Receives payment events from QuickBooks to sync payment status into FlexPrice.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleQuickbooksWebhook" method="post" path="/webhooks/quickbooks/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_quickbooks_webhook(tenant_id="<id>", environment_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `intuit_signature`                                                  | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | QuickBooks webhook signature                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_razorpay_webhook

Use as the Razorpay webhook endpoint URL. Receives payment capture and failure events to update invoice or payment status in FlexPrice.

### Example Usage

<!-- UsageSnippet language="python" operationID="handleRazorpayWebhook" method="post" path="/webhooks/razorpay/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_razorpay_webhook(tenant_id="<id>", environment_id="<id>", x_razorpay_signature="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `x_razorpay_signature`                                              | *str*                                                               | :heavy_check_mark:                                                  | Razorpay webhook signature                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |

## handle_stripe_webhook

Use as the Stripe webhook endpoint URL. Receives payment and customer events from Stripe to keep FlexPrice in sync (e.g. payment succeeded, customer created).

### Example Usage

<!-- UsageSnippet language="python" operationID="handleStripeWebhook" method="post" path="/webhooks/stripe/{tenant_id}/{environment_id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.webhooks.handle_stripe_webhook(tenant_id="<id>", environment_id="<id>", stripe_signature="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `tenant_id`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Tenant ID                                                           |
| `environment_id`                                                    | *str*                                                               | :heavy_check_mark:                                                  | Environment ID                                                      |
| `stripe_signature`                                                  | *str*                                                               | :heavy_check_mark:                                                  | Stripe webhook signature                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, Any]](../../models/.md)**

### Errors

| Error Type             | Status Code            | Content Type           |
| ---------------------- | ---------------------- | ---------------------- |
| errors.SDKDefaultError | 4XX, 5XX               | \*/\*                  |