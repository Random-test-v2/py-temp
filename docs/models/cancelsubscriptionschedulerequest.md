# CancelSubscriptionScheduleRequest


## Fields

| Field                                                                              | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `schedule_id_param`                                                                | *str*                                                                              | :heavy_check_mark:                                                                 | Schedule ID (optional if using request body)                                       |
| `body`                                                                             | [Optional[models.DtoCancelScheduleRequest]](../models/dtocancelschedulerequest.md) | :heavy_minus_sign:                                                                 | Cancel request (optional if using path parameter)                                  |