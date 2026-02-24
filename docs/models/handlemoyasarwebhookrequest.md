# HandleMoyasarWebhookRequest


## Fields

| Field                     | Type                      | Required                  | Description               |
| ------------------------- | ------------------------- | ------------------------- | ------------------------- |
| `tenant_id`               | *str*                     | :heavy_check_mark:        | Tenant ID                 |
| `environment_id`          | *str*                     | :heavy_check_mark:        | Environment ID            |
| `x_moyasar_signature`     | *Optional[str]*           | :heavy_minus_sign:        | Moyasar webhook signature |