# HandleNomodWebhookRequest


## Fields

| Field                                | Type                                 | Required                             | Description                          |
| ------------------------------------ | ------------------------------------ | ------------------------------------ | ------------------------------------ |
| `tenant_id`                          | *str*                                | :heavy_check_mark:                   | Tenant ID                            |
| `environment_id`                     | *str*                                | :heavy_check_mark:                   | Environment ID                       |
| `x_api_key`                          | *Optional[str]*                      | :heavy_minus_sign:                   | Nomod webhook secret (if configured) |