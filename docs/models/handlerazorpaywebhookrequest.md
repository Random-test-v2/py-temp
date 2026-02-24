# HandleRazorpayWebhookRequest


## Fields

| Field                      | Type                       | Required                   | Description                |
| -------------------------- | -------------------------- | -------------------------- | -------------------------- |
| `tenant_id`                | *str*                      | :heavy_check_mark:         | Tenant ID                  |
| `environment_id`           | *str*                      | :heavy_check_mark:         | Environment ID             |
| `x_razorpay_signature`     | *str*                      | :heavy_check_mark:         | Razorpay webhook signature |