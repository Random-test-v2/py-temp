# DtoClonePlanRequest


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `description`                                                        | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Description overrides the source plan's description when provided    |
| `display_order`                                                      | *Optional[int]*                                                      | :heavy_minus_sign:                                                   | DisplayOrder overrides the source plan's display order when provided |
| `lookup_key`                                                         | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | LookupKey is required and must be unique across published plans      |
| `metadata`                                                           | Dict[str, *str*]                                                     | :heavy_minus_sign:                                                   | N/A                                                                  |
| `name`                                                               | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Name is required and must be different from the source plan's name   |