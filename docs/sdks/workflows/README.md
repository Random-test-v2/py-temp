# Workflows

## Overview

### Available Operations

* [query_workflow](#query_workflow) - Query workflows

## query_workflow

Use when listing or auditing workflow runs (e.g. ops dashboard or debugging). Returns a paginated list; supports filtering by workflow type and status.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryWorkflow" method="post" path="/workflows/search" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.workflows.query_workflow()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `end_time`                                                                                              | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `entity`                                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | e.g. plan, invoice, subscription                                                                        |
| `entity_id`                                                                                             | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | e.g. plan_01ABC123                                                                                      |
| `expand`                                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `filters`                                                                                               | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]                               | :heavy_minus_sign:                                                                                      | filters allows complex filtering based on multiple fields (same as FeatureFilter)                       |
| `limit`                                                                                                 | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `offset`                                                                                                | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `order`                                                                                                 | [Optional[models.TypesWorkflowExecutionFilterOrder]](../../models/typesworkflowexecutionfilterorder.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `sort`                                                                                                  | List[[models.TypesSortCondition](../../models/typessortcondition.md)]                                   | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `start_time`                                                                                            | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `status`                                                                                                | [Optional[models.TypesStatus]](../../models/typesstatus.md)                                             | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `task_queue`                                                                                            | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `workflow_id`                                                                                           | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | Workflow-specific filters                                                                               |
| `workflow_status`                                                                                       | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | e.g. Running, Completed, Failed                                                                         |
| `workflow_type`                                                                                         | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |

### Response

**[models.DtoListWorkflowsResponse](../../models/dtolistworkflowsresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400                          | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |