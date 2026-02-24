# DtoCreateMeterRequest


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `aggregation`                                            | [models.MeterAggregation](../models/meteraggregation.md) | :heavy_check_mark:                                       | N/A                                                      |                                                          |
| `event_name`                                             | *str*                                                    | :heavy_check_mark:                                       | N/A                                                      | api_request                                              |
| `filters`                                                | List[[models.MeterFilter](../models/meterfilter.md)]     | :heavy_minus_sign:                                       | N/A                                                      |                                                          |
| `name`                                                   | *str*                                                    | :heavy_check_mark:                                       | N/A                                                      | API Usage Meter                                          |
| `reset_usage`                                            | [models.TypesResetUsage](../models/typesresetusage.md)   | :heavy_check_mark:                                       | N/A                                                      |                                                          |