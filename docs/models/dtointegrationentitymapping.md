# DtoIntegrationEntityMapping

Integration entity mapping for external provider systems


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `id`                                                                   | *str*                                                                  | :heavy_check_mark:                                                     | id is the external entity ID from the provider                         |
| `provider`                                                             | [models.Provider](../models/provider.md)                               | :heavy_check_mark:                                                     | provider is the integration provider name (e.g., "stripe", "razorpay") |