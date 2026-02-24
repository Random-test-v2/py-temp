# TriggerScheduledTaskRunRequest


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `id`                                                                                 | *str*                                                                                | :heavy_check_mark:                                                                   | Scheduled Task ID                                                                    |
| `body`                                                                               | [Optional[models.DtoTriggerForceRunRequest]](../models/dtotriggerforcerunrequest.md) | :heavy_minus_sign:                                                                   | Optional start and end time for custom range                                         |