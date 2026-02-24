# DtoListSubscriptionPausesResponse

Response object for listing subscription pauses with total count


## Fields

| Field                                                                                  | Type                                                                                   | Required                                                                               | Description                                                                            |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `items`                                                                                | List[[models.DtoSubscriptionPauseResponse](../models/dtosubscriptionpauseresponse.md)] | :heavy_minus_sign:                                                                     | List of subscription pause objects<br/>@Description Array of subscription pauses       |
| `total`                                                                                | *Optional[int]*                                                                        | :heavy_minus_sign:                                                                     | Total number of pauses<br/>@Description Total count of subscription pauses in the response |