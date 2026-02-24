# Coupons

## Overview

### Available Operations

* [create_coupon](#create_coupon) - Create coupon
* [query_coupon](#query_coupon) - Query coupons
* [get_coupon](#get_coupon) - Get coupon
* [update_coupon](#update_coupon) - Update coupon
* [delete_coupon](#delete_coupon) - Delete coupon

## create_coupon

Use when creating a discount (e.g. promo code or referral). Ideal for percent or fixed value, with optional validity and usage limits.

### Example Usage

<!-- UsageSnippet language="python" operationID="createCoupon" method="post" path="/coupons" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.coupons.create_coupon(cadence="repeated", name="<value>", type_="percentage")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `cadence`                                                           | [models.TypesCouponCadence](../../models/typescouponcadence.md)     | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `type`                                                              | [models.TypesCouponType](../../models/typescoupontype.md)           | :heavy_check_mark:                                                  | N/A                                                                 |
| `amount_off`                                                        | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `currency`                                                          | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `duration_in_periods`                                               | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `max_redemptions`                                                   | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `percentage_off`                                                    | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `redeem_after`                                                      | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `redeem_before`                                                     | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `rules`                                                             | Dict[str, *Any*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCouponResponse](../../models/dtocouponresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 401, 403, 404         | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## query_coupon

Use when listing or searching coupons (e.g. promo management). Returns a paginated list; supports filtering and sorting.

### Example Usage

<!-- UsageSnippet language="python" operationID="queryCoupon" method="post" path="/coupons/search" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.coupons.query_coupon()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `coupon_ids`                                                                      | List[*str*]                                                                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `expand`                                                                          | *Optional[str]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `filters`                                                                         | List[[models.TypesFilterCondition](../../models/typesfiltercondition.md)]         | :heavy_minus_sign:                                                                | N/A                                                                               |
| `limit`                                                                           | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `offset`                                                                          | *Optional[int]*                                                                   | :heavy_minus_sign:                                                                | N/A                                                                               |
| `order`                                                                           | [Optional[models.TypesCouponFilterOrder]](../../models/typescouponfilterorder.md) | :heavy_minus_sign:                                                                | N/A                                                                               |
| `sort`                                                                            | List[[models.TypesSortCondition](../../models/typessortcondition.md)]             | :heavy_minus_sign:                                                                | N/A                                                                               |
| `status`                                                                          | [Optional[models.TypesStatus]](../../models/typesstatus.md)                       | :heavy_minus_sign:                                                                | N/A                                                                               |
| `retries`                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                  | :heavy_minus_sign:                                                                | Configuration to override the default retry behavior of the client.               |

### Response

**[models.DtoListCouponsResponse](../../models/dtolistcouponsresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400                        | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## get_coupon

Use when you need to load a single coupon (e.g. for display or to validate a code).

### Example Usage

<!-- UsageSnippet language="python" operationID="getCoupon" method="get" path="/coupons/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.coupons.get_coupon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Coupon ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCouponResponse](../../models/dtocouponresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 404                   | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## update_coupon

Use when changing coupon config (e.g. value, validity, or usage limits).

### Example Usage

<!-- UsageSnippet language="python" operationID="updateCoupon" method="put" path="/coupons/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.coupons.update_coupon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Coupon ID                                                           |
| `metadata`                                                          | Dict[str, *str*]                                                    | :heavy_minus_sign:                                                  | N/A                                                                 |
| `name`                                                              | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.DtoCouponResponse](../../models/dtocouponresponse.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 401, 403, 404         | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |

## delete_coupon

Use when retiring a coupon (e.g. campaign ended). Returns 200 with success message.

### Example Usage

<!-- UsageSnippet language="python" operationID="deleteCoupon" method="delete" path="/coupons/{id}" -->
```python
from openapi import SDK


with SDK(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as sdk:

    res = sdk.coupons.delete_coupon(id="<id>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `id`                                                                | *str*                                                               | :heavy_check_mark:                                                  | Coupon ID                                                           |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Dict[str, str]](../../models/.md)**

### Errors

| Error Type                 | Status Code                | Content Type               |
| -------------------------- | -------------------------- | -------------------------- |
| errors.ErrorsErrorResponse | 400, 401, 403, 404         | application/json           |
| errors.ErrorsErrorResponse | 500                        | application/json           |
| errors.SDKDefaultError     | 4XX, 5XX                   | \*/\*                      |