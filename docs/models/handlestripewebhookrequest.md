# HandleStripeWebhookRequest


## Fields

| Field                    | Type                     | Required                 | Description              |
| ------------------------ | ------------------------ | ------------------------ | ------------------------ |
| `tenant_id`              | *str*                    | :heavy_check_mark:       | Tenant ID                |
| `environment_id`         | *str*                    | :heavy_check_mark:       | Environment ID           |
| `stripe_signature`       | *str*                    | :heavy_check_mark:       | Stripe webhook signature |