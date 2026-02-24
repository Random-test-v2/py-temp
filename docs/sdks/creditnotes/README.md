# CreditNotes

## Overview

### Available Operations

* [create_credit_note](#create_credit_note) - Create credit note
* [get_credit_note](#get_credit_note) - Get credit note
* [process_credit_note](#process_credit_note) - Finalize credit note
* [void_credit_note](#void_credit_note) - Void credit note

## create_credit_note

Use when issuing a refund or adjustment (e.g. customer dispute or proration). Links to an invoice; create as draft then finalize.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCreditNote" method="post" path="/creditnotes" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.credit_notes.create_credit_note(invoice_id="<id>", reason="FRAUDULENT", process_credit_note=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `invoice_id`                                                                                          | *str*                                                                                                 | :heavy_check_mark:                                                                                    | invoice_id is the unique identifier of the invoice this credit note is applied to                     |
| `reason`                                                                                              | [models.TypesCreditNoteReason](../../models/typescreditnotereason.md)                                 | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `credit_note_number`                                                                                  | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | credit_note_number is an optional human-readable identifier for the credit note                       |
| `idempotency_key`                                                                                     | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | idempotency_key is an optional key used to prevent duplicate credit note creation                     |
| `line_items`                                                                                          | List[[models.DtoCreateCreditNoteLineItemRequest](../../models/dtocreatecreditnotelineitemrequest.md)] | :heavy_minus_sign:                                                                                    | line_items contains the individual line items that make up this credit note (minimum 1 required)      |
| `memo`                                                                                                | *Optional[str]*                                                                                       | :heavy_minus_sign:                                                                                    | memo is an optional free-text field for additional notes about the credit note                        |
| `metadata`                                                                                            | Dict[str, *str*]                                                                                      | :heavy_minus_sign:                                                                                    | N/A                                                                                                   |
| `process_credit_note`                                                                                 | *Optional[bool]*                                                                                      | :heavy_minus_sign:                                                                                    | process_credit_note is a flag to process the credit note after creation                               |
| `retries`                                                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                      | :heavy_minus_sign:                                                                                    | Configuration to override the default retry behavior of the client.                                   |

### Response

**[models.DtoCreditNoteResponse](../../models/dtocreditnoteresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 401, 403, 404           | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## get_credit_note

Use when you need to load a single credit note (e.g. for display or reconciliation).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCreditNote" method="get" path="/creditnotes/{id}" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.credit_notes.get_credit_note(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Credit note ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreditNoteResponse](../../models/dtocreditnoteresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 404                     | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## process_credit_note

Use when locking a draft credit note and applying the credit (e.g. after approval). Once finalized, applied per billing provider.

### Example Usage

<!-- UsageSnippet language="python" operationID="processCreditNote" method="post" path="/creditnotes/{id}/finalize" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.credit_notes.process_credit_note(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Credit note ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreditNoteResponse](../../models/dtocreditnoteresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 401, 403, 404           | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |

## void_credit_note

Use when cancelling a draft credit note (e.g. created by mistake). Only draft credit notes can be voided.

### Example Usage

<!-- UsageSnippet language="python" operationID="voidCreditNote" method="post" path="/creditnotes/{id}/void" -->
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.credit_notes.void_credit_note(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Credit note ID                                                      |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCreditNoteResponse](../../models/dtocreditnoteresponse.md)**

### Errors

| Error Type                   | Status Code                  | Content Type                 |
| ---------------------------- | ---------------------------- | ---------------------------- |
| errors.ErrorsErrorResponse   | 400, 401, 403, 404           | application/json             |
| errors.ErrorsErrorResponse   | 500                          | application/json             |
| errors.FlexpriceDefaultError | 4XX, 5XX                     | \*/\*                        |