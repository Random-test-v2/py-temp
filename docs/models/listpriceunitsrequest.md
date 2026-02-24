# ListPriceUnitsRequest


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `status`                                                                 | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Filter by status                                                         |
| `limit`                                                                  | *Optional[int]*                                                          | :heavy_minus_sign:                                                       | Limit number of results                                                  |
| `offset`                                                                 | *Optional[int]*                                                          | :heavy_minus_sign:                                                       | Offset for pagination                                                    |
| `sort`                                                                   | *Optional[str]*                                                          | :heavy_minus_sign:                                                       | Sort field                                                               |
| `order`                                                                  | [Optional[models.ListPriceUnitsOrder]](../models/listpriceunitsorder.md) | :heavy_minus_sign:                                                       | Sort order                                                               |