# DtoUserResponse


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `email`                                                              | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | Empty for service accounts                                           |
| `id`                                                                 | *Optional[str]*                                                      | :heavy_minus_sign:                                                   | N/A                                                                  |
| `roles`                                                              | List[*str*]                                                          | :heavy_minus_sign:                                                   | N/A                                                                  |
| `tenant`                                                             | [Optional[models.DtoTenantResponse]](../models/dtotenantresponse.md) | :heavy_minus_sign:                                                   | N/A                                                                  |
| `type`                                                               | [Optional[models.TypesUserType]](../models/typesusertype.md)         | :heavy_minus_sign:                                                   | N/A                                                                  |