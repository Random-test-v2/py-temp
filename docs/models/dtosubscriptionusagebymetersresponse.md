# DtoSubscriptionUsageByMetersResponse


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `amount`                                               | *Optional[float]*                                      | :heavy_minus_sign:                                     | N/A                                                    |
| `currency`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `display_amount`                                       | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `filter_values`                                        | Dict[str, List[*str*]]                                 | :heavy_minus_sign:                                     | N/A                                                    |
| `is_overage`                                           | *Optional[bool]*                                       | :heavy_minus_sign:                                     | Whether this charge is at overage rate                 |
| `meter_display_name`                                   | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `meter_id`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `overage_factor`                                       | *Optional[float]*                                      | :heavy_minus_sign:                                     | Factor applied to this charge if in overage            |
| `price`                                                | [Optional[models.PricePrice]](../models/priceprice.md) | :heavy_minus_sign:                                     | N/A                                                    |
| `quantity`                                             | *Optional[float]*                                      | :heavy_minus_sign:                                     | N/A                                                    |