# Tasks

## Overview

### Available Operations

* [list_tasks](#list_tasks) - List tasks
* [create_task](#create_task) - Create a new task
* [get_task_result](#get_task_result) - Get task processing result
* [get_task](#get_task) - Get a task
* [download_task_export](#download_task_export) - Download task export file
* [update_task_status](#update_task_status) - Update task status

## list_tasks

Use when listing or searching async tasks (e.g. admin queue view). Returns list with optional filtering.

### Example Usage

<!-- UsageSnippet language="python" operationID="listTasks" method="get" path="/tasks" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.list_tasks()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `created_by`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `end_time`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `entity_type`                                                       | [Optional[models.EntityType]](../../models/entitytype.md)           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `expand`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `order`                                                             | [Optional[models.ListTasksOrder]](../../models/listtasksorder.md)   | :heavy_minus_sign:                                                  | N/A                                                                 |
| `scheduled_task_id`                                                 | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `sort`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `start_time`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `status`                                                            | [Optional[models.ListTasksStatus]](../../models/listtasksstatus.md) | :heavy_minus_sign:                                                  | N/A                                                                 |
| `task_status`                                                       | [Optional[models.TaskStatus]](../../models/taskstatus.md)           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `task_type`                                                         | [Optional[models.TaskType]](../../models/tasktype.md)               | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoListTasksResponse](../../models/dtolisttasksresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## create_task

Use when submitting a file or job for async processing (e.g. export or import). Returns task ID to poll for status and result.

### Example Usage

<!-- UsageSnippet language="python" operationID="createTask" method="post" path="/tasks" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.create_task(entity_type="FEATURES", file_type="JSON", file_url="https://rural-typeface.org", task_type="IMPORT")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `entity_type`                                                       | [models.TypesEntityType](../../models/typesentitytype.md)           | :heavy_check_mark:                                                  | N/A                                                                 |
| `file_type`                                                         | [models.TypesFileType](../../models/typesfiletype.md)               | :heavy_check_mark:                                                  | N/A                                                                 |
| `file_url`                                                          | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `task_type`                                                         | [models.TypesTaskType](../../models/typestasktype.md)               | :heavy_check_mark:                                                  | N/A                                                                 |
| `file_name`                                                         | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaskResponse](../../models/dtotaskresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_task_result

Use when fetching the outcome of a completed task (e.g. export URL or error message). Call after task status is complete.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTaskResult" method="get" path="/tasks/result" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.get_task_result(workflow_id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workflow_id`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Workflow ID                                                         |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ModelsTemporalWorkflowResult](../../models/modelstemporalworkflowresult.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_task

Use when checking task status or progress (e.g. polling after create). Returns task by ID.

### Example Usage

<!-- UsageSnippet language="python" operationID="getTask" method="get" path="/tasks/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.get_task(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Task ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoTaskResponse](../../models/dtotaskresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## download_task_export

Use when letting a user download an exported file (e.g. report or data export). Returns a presigned URL; supports FlexPrice or customer-owned S3.

### Example Usage

<!-- UsageSnippet language="python" operationID="downloadTaskExport" method="get" path="/tasks/{id}/download" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.download_task_export(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Task ID                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, str]](../../models/.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_task_status

Use when updating task status (e.g. marking complete or failed from a worker). Typically called by backend processors.

### Example Usage

<!-- UsageSnippet language="python" operationID="updateTaskStatus" method="put" path="/tasks/{id}/status" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.tasks.update_task_status(id="<id>", task_status="PROCESSING")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Task ID                                                             |
| `task_status`                                                       | [models.TypesTaskStatus](../../models/typestaskstatus.md)           | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoSuccessResponse](../../models/dtosuccessresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |