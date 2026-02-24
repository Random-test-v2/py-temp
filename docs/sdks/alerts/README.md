# Alerts

## Overview

### Available Operations

* [query_alert_log](#query_alert_log) - Query alert logs

## query_alert_log

Use when viewing or searching alert history (e.g. support triage or customer-facing alert log). Returns a paginated list; supports filtering by type, customer, subscription.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryAlertLog" method="post" path="/alerts/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.alerts.query_alert_log()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `alert_status`                                                                        | [Optional[models.TypesAlertState]](../../models/typesalertstate.md)                   | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `alert_type`                                                                          | [Optional[models.TypesAlertType]](../../models/typesalerttype.md)                     | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `customer_id`                                                                         | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `end_time`                                                                            | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `entity_id`                                                                           | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `entity_type`                                                                         | [Optional[models.TypesAlertEntityType]](../../models/typesalertentitytype.md)         | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `expand`                                                                              | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `filters`                                                                             | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]             | :heavy_minus_sign:                                                                    | filters allows complex filtering based on multiple fields                             |
| `limit`                                                                               | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `offset`                                                                              | *Optional[int]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `order`                                                                               | [Optional[models.TypesAlertLogFilterOrder]](../../models/typesalertlogfilterorder.md) | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `sort`                                                                                | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                 | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `start_time`                                                                          | *Optional[str]*                                                                       | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `status`                                                                              | [Optional[models.TypesStatus]](../../models/typesstatus.md)                           | :heavy_minus_sign:                                                                    | N/A                                                                                   |
| `retries`                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                      | :heavy_minus_sign:                                                                    | Configuration to override the default retry behavior of the client.                   |

### Response

**[models.DtoListAlertLogsResponse](../../models/dtolistalertlogsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |