# Users

## Overview

### Available Operations

* [create_user](#create_user) - Create service account
* [get_user_info](#get_user_info) - Get current user
* [query_user](#query_user) - Query users

## create_user

Use when provisioning API access for automation, CI/CD pipelines, or headless integrations that need scoped API keys.

### Example Usage

<!-- UsageSnippet language="python" operationID="createUser" method="post" path="/users" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.users.create_user(roles=[], type_="user")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `roles`                                                             | List[*str*]                                                         | :heavy_check_mark:                                                  | Roles are required                                                  |
| `type`                                                              | [models.TypesUserType](../../models/typesusertype.md)               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoUserResponse](../../models/dtouserresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_user_info

Use to show the logged-in user's profile in the UI or to check permissions and roles for the current session.

### Example Usage

<!-- UsageSnippet language="python" operationID="getUserInfo" method="get" path="/users/me" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.users.get_user_info()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoUserResponse](../../models/dtouserresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 401                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_user

Use when listing or searching service accounts in an admin UI, or when auditing who has API access and which roles they have.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryUser" method="post" path="/users/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.users.query_user()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `end_time`                                                                    | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `expand`                                                                      | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `filters`                                                                     | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]     | :heavy_minus_sign:                                                            | filters allows complex filtering based on multiple fields                     |
| `limit`                                                                       | *Optional[int]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `offset`                                                                      | *Optional[int]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `order`                                                                       | [Optional[models.TypesUserFilterOrder]](../../models/typesuserfilterorder.md) | :heavy_minus_sign:                                                            | N/A                                                                           |
| `roles`                                                                       | List[*str*]                                                                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `sort`                                                                        | List[[models.TypesSortCondition](../../models/typessortcondition.md)]         | :heavy_minus_sign:                                                            | N/A                                                                           |
| `start_time`                                                                  | *Optional[str]*                                                               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `status`                                                                      | [Optional[models.TypesStatus]](../../models/typesstatus.md)                   | :heavy_minus_sign:                                                            | N/A                                                                           |
| `type`                                                                        | [Optional[models.TypesUserType]](../../models/typesusertype.md)               | :heavy_minus_sign:                                                            | N/A                                                                           |
| `user_ids`                                                                    | List[*str*]                                                                   | :heavy_minus_sign:                                                            | Specific filters for users                                                    |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Response

**[models.DtoListUsersResponse](../../models/dtolistusersresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |