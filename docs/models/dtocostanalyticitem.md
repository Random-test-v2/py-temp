# DtoCostAnalyticItem


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `cost_by_period`                                       | List[[models.DtoCostPoint](../models/dtocostpoint.md)] | :heavy_minus_sign:                                     | Breakdown                                              |
| `costsheet_id`                                         | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `currency`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | Metadata                                               |
| `customer_id`                                          | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `external_customer_id`                                 | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `meter`                                                | [Optional[models.MeterMeter]](../models/metermeter.md) | :heavy_minus_sign:                                     | N/A                                                    |
| `meter_id`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `meter_name`                                           | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `price`                                                | [Optional[models.PricePrice]](../models/priceprice.md) | :heavy_minus_sign:                                     | N/A                                                    |
| `price_id`                                             | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `properties`                                           | Dict[str, *str*]                                       | :heavy_minus_sign:                                     | N/A                                                    |
| `source`                                               | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `total_cost`                                           | *Optional[str]*                                        | :heavy_minus_sign:                                     | Aggregated metrics                                     |
| `total_events`                                         | *Optional[int]*                                        | :heavy_minus_sign:                                     | N/A                                                    |
| `total_quantity`                                       | *Optional[str]*                                        | :heavy_minus_sign:                                     | N/A                                                    |