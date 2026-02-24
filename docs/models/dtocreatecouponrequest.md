# DtoCreateCouponRequest


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `amount_off`                                                 | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `cadence`                                                    | [models.TypesCouponCadence](../models/typescouponcadence.md) | :heavy_check_mark:                                           | N/A                                                          |
| `currency`                                                   | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `duration_in_periods`                                        | *Optional[int]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `max_redemptions`                                            | *Optional[int]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `metadata`                                                   | Dict[str, *str*]                                             | :heavy_minus_sign:                                           | N/A                                                          |
| `name`                                                       | *str*                                                        | :heavy_check_mark:                                           | N/A                                                          |
| `percentage_off`                                             | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `redeem_after`                                               | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `redeem_before`                                              | *Optional[str]*                                              | :heavy_minus_sign:                                           | N/A                                                          |
| `rules`                                                      | Dict[str, *Any*]                                             | :heavy_minus_sign:                                           | N/A                                                          |
| `type`                                                       | [models.TypesCouponType](../models/typescoupontype.md)       | :heavy_check_mark:                                           | N/A                                                          |