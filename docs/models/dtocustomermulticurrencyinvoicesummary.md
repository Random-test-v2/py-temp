# DtoCustomerMultiCurrencyInvoiceSummary


## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `customer_id`                                                                    | *Optional[str]*                                                                  | :heavy_minus_sign:                                                               | customer_id is the unique identifier of the customer                             |
| `default_currency`                                                               | *Optional[str]*                                                                  | :heavy_minus_sign:                                                               | default_currency is the primary currency for this customer                       |
| `summaries`                                                                      | List[[models.DtoCustomerInvoiceSummary](../models/dtocustomerinvoicesummary.md)] | :heavy_minus_sign:                                                               | summaries contains the invoice summaries for each currency                       |