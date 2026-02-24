# flexprice-py

Developer-friendly & type-safe Python SDK specifically catered to leverage *flexprice-py* API.

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=flexprice-py&utm_campaign=python)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/flexprice/prod). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Flexprice API: Flexprice API provides billing, metering, and subscription management for SaaS and usage-based products. Use it to manage customers, plans, invoices, payments, usage events, and entitlements. Authenticate with an API key in the x-api-key header.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [flexprice-py](#flexprice-py)
  * [SDK Installation](#sdk-installation)
  * [IDE Support](#ide-support)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Custom HTTP Client](#custom-http-client)
  * [Resource Management](#resource-management)
  * [Debugging](#debugging)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!NOTE]
> **Python version upgrade policy**
>
> Once a Python version reaches its [official end of life date](https://devguide.python.org/versions/), a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with *uv*, *pip*, or *poetry* package managers.

### uv

*uv* is a fast Python package installer and resolver, designed as a drop-in replacement for pip and pip-tools. It's recommended for its speed and modern Python tooling capabilities.

```bash
uv add flexprice-py
```

### PIP

*PIP* is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```bash
pip install flexprice-py
```

### Poetry

*Poetry* is a modern tool that simplifies dependency management and package publishing by using a single `pyproject.toml` file to handle project metadata and dependencies.

```bash
poetry add flexprice-py
```

### Shell and script usage with `uv`

You can use this SDK in a Python shell with [uv](https://docs.astral.sh/uv/) and the `uvx` command that comes with it like so:

```shell
uvx --from flexprice-py python
```

It's also possible to write a standalone Python script without needing to set up a whole project like so:

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.10"
# dependencies = [
#     "flexprice-py",
# ]
# ///

from flexprice_py import Flexprice

sdk = Flexprice(
  # SDK arguments
)

# Rest of script here...
```

Once that is saved to a file, you can run it with `uv run script.py` where
`script.py` can be replaced with the actual file name.
<!-- End SDK Installation [installation] -->

<!-- Start IDE Support [idesupport] -->
## IDE Support

### PyCharm

Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

- [PyCharm Pydantic Plugin](https://docs.pydantic.dev/latest/integrations/pycharm/)
<!-- End IDE Support [idesupport] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```python
# Synchronous Example
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance")

    # Handle response
    print(res)
```

</br>

The same SDK client can also be used to make asynchronous requests by importing asyncio.

```python
# Asynchronous Example
import asyncio
from flexprice_py import Flexprice

async def main():

    async with Flexprice(
        server_url="https://api.example.com",
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as flexprice:

        res = await flexprice.addons.create_addon_async(lookup_key="<value>", name="<value>", type_="multiple_instance")

        # Handle response
        print(res)

asyncio.run(main())
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name           | Type   | Scheme  |
| -------------- | ------ | ------- |
| `api_key_auth` | apiKey | API key |

To authenticate with the API the `api_key_auth` parameter must be set when initializing the SDK client instance. For example:
```python
from flexprice_py import Flexprice


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance")

    # Handle response
    print(res)

```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [Addons](docs/sdks/addons/README.md)

* [create_addon](docs/sdks/addons/README.md#create_addon) - Create addon
* [get_addon_by_lookup_key](docs/sdks/addons/README.md#get_addon_by_lookup_key) - Get addon by lookup key
* [query_addon](docs/sdks/addons/README.md#query_addon) - Query addons
* [get_addon](docs/sdks/addons/README.md#get_addon) - Get addon
* [update_addon](docs/sdks/addons/README.md#update_addon) - Update addon
* [delete_addon](docs/sdks/addons/README.md#delete_addon) - Delete addon

### [Alerts](docs/sdks/alerts/README.md)

* [query_alert_log](docs/sdks/alerts/README.md#query_alert_log) - Query alert logs

### [Costs](docs/sdks/costs/README.md)

* [create_costsheet](docs/sdks/costs/README.md#create_costsheet) - Create costsheet
* [get_active_costsheet](docs/sdks/costs/README.md#get_active_costsheet) - Get active costsheet
* [get_detailed_cost_analytics](docs/sdks/costs/README.md#get_detailed_cost_analytics) - Get combined revenue and cost analytics
* [get_detailed_cost_analytics_v2](docs/sdks/costs/README.md#get_detailed_cost_analytics_v2) - Get combined revenue and cost analytics (V2)
* [query_costsheet](docs/sdks/costs/README.md#query_costsheet) - Query costsheets
* [get_costsheet](docs/sdks/costs/README.md#get_costsheet) - Get costsheet
* [update_costsheet](docs/sdks/costs/README.md#update_costsheet) - Update costsheet
* [delete_costsheet](docs/sdks/costs/README.md#delete_costsheet) - Delete costsheet

### [Coupons](docs/sdks/coupons/README.md)

* [create_coupon](docs/sdks/coupons/README.md#create_coupon) - Create coupon
* [query_coupon](docs/sdks/coupons/README.md#query_coupon) - Query coupons
* [get_coupon](docs/sdks/coupons/README.md#get_coupon) - Get coupon
* [update_coupon](docs/sdks/coupons/README.md#update_coupon) - Update coupon
* [delete_coupon](docs/sdks/coupons/README.md#delete_coupon) - Delete coupon

### [CreditGrants](docs/sdks/creditgrants/README.md)

* [create_credit_grant](docs/sdks/creditgrants/README.md#create_credit_grant) - Create credit grant
* [get_credit_grant](docs/sdks/creditgrants/README.md#get_credit_grant) - Get credit grant
* [update_credit_grant](docs/sdks/creditgrants/README.md#update_credit_grant) - Update credit grant
* [delete_credit_grant](docs/sdks/creditgrants/README.md#delete_credit_grant) - Delete credit grant
* [get_plan_credit_grants](docs/sdks/creditgrants/README.md#get_plan_credit_grants) - Get plan credit grants

### [CreditNotes](docs/sdks/creditnotes/README.md)

* [create_credit_note](docs/sdks/creditnotes/README.md#create_credit_note) - Create credit note
* [get_credit_note](docs/sdks/creditnotes/README.md#get_credit_note) - Get credit note
* [process_credit_note](docs/sdks/creditnotes/README.md#process_credit_note) - Finalize credit note
* [void_credit_note](docs/sdks/creditnotes/README.md#void_credit_note) - Void credit note

### [Customers](docs/sdks/customers/README.md)

* [update_customer](docs/sdks/customers/README.md#update_customer) - Update customer
* [create_customer](docs/sdks/customers/README.md#create_customer) - Create customer
* [get_customer_by_external_id](docs/sdks/customers/README.md#get_customer_by_external_id) - Get customer by external ID
* [query_customer](docs/sdks/customers/README.md#query_customer) - Query customers
* [get_customer_usage_summary](docs/sdks/customers/README.md#get_customer_usage_summary) - Get customer usage summary
* [get_customer](docs/sdks/customers/README.md#get_customer) - Get customer
* [delete_customer](docs/sdks/customers/README.md#delete_customer) - Delete customer
* [get_customer_entitlements](docs/sdks/customers/README.md#get_customer_entitlements) - Get customer entitlements
* [get_customer_upcoming_grants](docs/sdks/customers/README.md#get_customer_upcoming_grants) - Get upcoming credit grant applications

### [Entitlements](docs/sdks/entitlements/README.md)

* [get_addon_entitlements](docs/sdks/entitlements/README.md#get_addon_entitlements) - Get addon entitlements
* [create_entitlement](docs/sdks/entitlements/README.md#create_entitlement) - Create entitlement
* [create_entitlements_bulk](docs/sdks/entitlements/README.md#create_entitlements_bulk) - Create entitlements in bulk
* [query_entitlement](docs/sdks/entitlements/README.md#query_entitlement) - Query entitlements
* [get_entitlement](docs/sdks/entitlements/README.md#get_entitlement) - Get entitlement
* [update_entitlement](docs/sdks/entitlements/README.md#update_entitlement) - Update entitlement
* [delete_entitlement](docs/sdks/entitlements/README.md#delete_entitlement) - Delete entitlement
* [get_plan_entitlements](docs/sdks/entitlements/README.md#get_plan_entitlements) - Get plan entitlements

### [EntityIntegrationMappings](docs/sdks/entityintegrationmappings/README.md)

* [create_entity_integration_mapping](docs/sdks/entityintegrationmappings/README.md#create_entity_integration_mapping) - Create entity integration mapping
* [delete_entity_integration_mapping](docs/sdks/entityintegrationmappings/README.md#delete_entity_integration_mapping) - Delete entity integration mapping

### [Environments](docs/sdks/environments/README.md)

* [create_environment](docs/sdks/environments/README.md#create_environment) - Create environment
* [update_environment](docs/sdks/environments/README.md#update_environment) - Update environment

### [Events](docs/sdks/events/README.md)

* [ingest_event](docs/sdks/events/README.md#ingest_event) - Ingest event
* [get_usage_analytics](docs/sdks/events/README.md#get_usage_analytics) - Get usage analytics
* [ingest_events_bulk](docs/sdks/events/README.md#ingest_events_bulk) - Bulk ingest events
* [get_huggingface_inference_data](docs/sdks/events/README.md#get_huggingface_inference_data) - Get Hugging Face inference data
* [list_raw_events](docs/sdks/events/README.md#list_raw_events) - List raw events
* [get_usage_statistics](docs/sdks/events/README.md#get_usage_statistics) - Get usage statistics
* [get_usage_by_meter](docs/sdks/events/README.md#get_usage_by_meter) - Get usage by meter
* [get_event](docs/sdks/events/README.md#get_event) - Get event

### [Features](docs/sdks/features/README.md)

* [create_feature](docs/sdks/features/README.md#create_feature) - Create feature
* [query_feature](docs/sdks/features/README.md#query_feature) - Query features
* [update_feature](docs/sdks/features/README.md#update_feature) - Update feature
* [delete_feature](docs/sdks/features/README.md#delete_feature) - Delete feature

### [Groups](docs/sdks/groups/README.md)

* [create_group](docs/sdks/groups/README.md#create_group) - Create group
* [query_group](docs/sdks/groups/README.md#query_group) - Query groups
* [get_group](docs/sdks/groups/README.md#get_group) - Get group
* [delete_group](docs/sdks/groups/README.md#delete_group) - Delete group

### [Integrations](docs/sdks/integrations/README.md)

* [get_integration](docs/sdks/integrations/README.md#get_integration) - Get integration details
* [create_or_update_integration](docs/sdks/integrations/README.md#create_or_update_integration) - Create or update an integration
* [list_linked_integrations](docs/sdks/integrations/README.md#list_linked_integrations) - List linked integrations
* [delete_integration](docs/sdks/integrations/README.md#delete_integration) - Delete an integration

### [Invoices](docs/sdks/invoices/README.md)

* [get_customer_invoice_summary](docs/sdks/invoices/README.md#get_customer_invoice_summary) - Get customer invoice summary
* [create_invoice](docs/sdks/invoices/README.md#create_invoice) - Create one-off invoice
* [get_invoice_preview](docs/sdks/invoices/README.md#get_invoice_preview) - Get invoice preview
* [query_invoice](docs/sdks/invoices/README.md#query_invoice) - Query invoices
* [get_invoice](docs/sdks/invoices/README.md#get_invoice) - Get invoice
* [update_invoice](docs/sdks/invoices/README.md#update_invoice) - Update invoice
* [trigger_invoice_comms_webhook](docs/sdks/invoices/README.md#trigger_invoice_comms_webhook) - Trigger invoice communication webhook
* [finalize_invoice](docs/sdks/invoices/README.md#finalize_invoice) - Finalize invoice
* [update_invoice_payment_status](docs/sdks/invoices/README.md#update_invoice_payment_status) - Update invoice payment status
* [attempt_invoice_payment](docs/sdks/invoices/README.md#attempt_invoice_payment) - Attempt invoice payment
* [get_invoice_pdf](docs/sdks/invoices/README.md#get_invoice_pdf) - Get invoice PDF
* [recalculate_invoice](docs/sdks/invoices/README.md#recalculate_invoice) - Recalculate invoice
* [void_invoice](docs/sdks/invoices/README.md#void_invoice) - Void invoice

### [Payments](docs/sdks/payments/README.md)

* [list_payments](docs/sdks/payments/README.md#list_payments) - List payments
* [create_payment](docs/sdks/payments/README.md#create_payment) - Create payment
* [get_payment](docs/sdks/payments/README.md#get_payment) - Get payment
* [update_payment](docs/sdks/payments/README.md#update_payment) - Update payment
* [delete_payment](docs/sdks/payments/README.md#delete_payment) - Delete payment
* [process_payment](docs/sdks/payments/README.md#process_payment) - Process payment

### [Plans](docs/sdks/plans/README.md)

* [create_plan](docs/sdks/plans/README.md#create_plan) - Create plan
* [query_plan](docs/sdks/plans/README.md#query_plan) - Query plans
* [get_plan](docs/sdks/plans/README.md#get_plan) - Get plan
* [update_plan](docs/sdks/plans/README.md#update_plan) - Update plan
* [delete_plan](docs/sdks/plans/README.md#delete_plan) - Delete plan
* [sync_plan_prices](docs/sdks/plans/README.md#sync_plan_prices) - Synchronize plan prices

### [PriceUnits](docs/sdks/priceunits/README.md)

* [list_price_units](docs/sdks/priceunits/README.md#list_price_units) - List price units
* [create_price_unit](docs/sdks/priceunits/README.md#create_price_unit) - Create price unit
* [get_price_unit_by_code](docs/sdks/priceunits/README.md#get_price_unit_by_code) - Get price unit by code
* [query_price_unit](docs/sdks/priceunits/README.md#query_price_unit) - Query price units
* [get_price_unit](docs/sdks/priceunits/README.md#get_price_unit) - Get price unit
* [update_price_unit](docs/sdks/priceunits/README.md#update_price_unit) - Update price unit
* [delete_price_unit](docs/sdks/priceunits/README.md#delete_price_unit) - Delete price unit

### [Prices](docs/sdks/prices/README.md)

* [create_price](docs/sdks/prices/README.md#create_price) - Create price
* [create_prices_bulk](docs/sdks/prices/README.md#create_prices_bulk) - Create prices in bulk
* [get_price_by_lookup_key](docs/sdks/prices/README.md#get_price_by_lookup_key) - Get price by lookup key
* [query_price](docs/sdks/prices/README.md#query_price) - Query prices
* [get_price](docs/sdks/prices/README.md#get_price) - Get price
* [update_price](docs/sdks/prices/README.md#update_price) - Update price
* [delete_price](docs/sdks/prices/README.md#delete_price) - Delete price

### [Rbac](docs/sdks/rbac/README.md)

* [list_rbac_roles](docs/sdks/rbac/README.md#list_rbac_roles) - List all RBAC roles
* [get_rbac_role](docs/sdks/rbac/README.md#get_rbac_role) - Get a specific RBAC role

### [ScheduledTasks](docs/sdks/scheduledtasks/README.md)

* [list_scheduled_tasks](docs/sdks/scheduledtasks/README.md#list_scheduled_tasks) - List scheduled tasks
* [create_scheduled_task](docs/sdks/scheduledtasks/README.md#create_scheduled_task) - Create scheduled task
* [schedule_update_billing_period](docs/sdks/scheduledtasks/README.md#schedule_update_billing_period) - Schedule update billing period
* [get_scheduled_task](docs/sdks/scheduledtasks/README.md#get_scheduled_task) - Get scheduled task
* [update_scheduled_task](docs/sdks/scheduledtasks/README.md#update_scheduled_task) - Update a scheduled task
* [delete_scheduled_task](docs/sdks/scheduledtasks/README.md#delete_scheduled_task) - Delete a scheduled task
* [trigger_scheduled_task_run](docs/sdks/scheduledtasks/README.md#trigger_scheduled_task_run) - Trigger force run

### [Secrets](docs/sdks/secrets/README.md)

* [list_api_keys](docs/sdks/secrets/README.md#list_api_keys) - List API keys
* [create_api_key](docs/sdks/secrets/README.md#create_api_key) - Create a new API key
* [delete_api_key](docs/sdks/secrets/README.md#delete_api_key) - Delete an API key

### [Subscriptions](docs/sdks/subscriptions/README.md)

* [create_subscription](docs/sdks/subscriptions/README.md#create_subscription) - Create subscription
* [add_subscription_addon](docs/sdks/subscriptions/README.md#add_subscription_addon) - Add addon to subscription
* [remove_subscription_addon](docs/sdks/subscriptions/README.md#remove_subscription_addon) - Remove addon from subscription
* [update_subscription_line_item](docs/sdks/subscriptions/README.md#update_subscription_line_item) - Update subscription line item
* [delete_subscription_line_item](docs/sdks/subscriptions/README.md#delete_subscription_line_item) - Delete subscription line item
* [query_subscription](docs/sdks/subscriptions/README.md#query_subscription) - Query subscriptions
* [get_subscription_usage](docs/sdks/subscriptions/README.md#get_subscription_usage) - Get usage by subscription
* [get_subscription](docs/sdks/subscriptions/README.md#get_subscription) - Get subscription
* [update_subscription](docs/sdks/subscriptions/README.md#update_subscription) - Update subscription
* [activate_subscription](docs/sdks/subscriptions/README.md#activate_subscription) - Activate draft subscription
* [get_subscription_addon_associations](docs/sdks/subscriptions/README.md#get_subscription_addon_associations) - Get active addon associations
* [cancel_subscription](docs/sdks/subscriptions/README.md#cancel_subscription) - Cancel subscription
* [execute_subscription_change](docs/sdks/subscriptions/README.md#execute_subscription_change) - Execute subscription plan change
* [preview_subscription_change](docs/sdks/subscriptions/README.md#preview_subscription_change) - Preview subscription plan change
* [get_subscription_entitlements](docs/sdks/subscriptions/README.md#get_subscription_entitlements) - Get subscription entitlements
* [get_subscription_upcoming_grants](docs/sdks/subscriptions/README.md#get_subscription_upcoming_grants) - Get upcoming credit grant applications
* [create_subscription_line_item](docs/sdks/subscriptions/README.md#create_subscription_line_item) - Create subscription line item
* [pause_subscription](docs/sdks/subscriptions/README.md#pause_subscription) - Pause a subscription
* [list_subscription_pauses](docs/sdks/subscriptions/README.md#list_subscription_pauses) - List all pauses for a subscription
* [resume_subscription](docs/sdks/subscriptions/README.md#resume_subscription) - Resume a paused subscription
* [get_subscription_v2](docs/sdks/subscriptions/README.md#get_subscription_v2) - Get subscription (V2)
* [list_all_subscription_schedules](docs/sdks/subscriptions/README.md#list_all_subscription_schedules) - List all subscription schedules
* [get_subscription_schedule](docs/sdks/subscriptions/README.md#get_subscription_schedule) - Get subscription schedule
* [cancel_subscription_schedule](docs/sdks/subscriptions/README.md#cancel_subscription_schedule) - Cancel subscription schedule
* [list_subscription_schedules](docs/sdks/subscriptions/README.md#list_subscription_schedules) - List subscription schedules

### [Tasks](docs/sdks/tasks/README.md)

* [list_tasks](docs/sdks/tasks/README.md#list_tasks) - List tasks
* [create_task](docs/sdks/tasks/README.md#create_task) - Create a new task
* [get_task_result](docs/sdks/tasks/README.md#get_task_result) - Get task processing result
* [get_task](docs/sdks/tasks/README.md#get_task) - Get a task
* [download_task_export](docs/sdks/tasks/README.md#download_task_export) - Download task export file
* [update_task_status](docs/sdks/tasks/README.md#update_task_status) - Update task status

### [TaxAssociations](docs/sdks/taxassociations/README.md)

* [list_tax_associations](docs/sdks/taxassociations/README.md#list_tax_associations) - List tax associations
* [create_tax_association](docs/sdks/taxassociations/README.md#create_tax_association) - Create Tax Association
* [get_tax_association](docs/sdks/taxassociations/README.md#get_tax_association) - Get Tax Association
* [update_tax_association](docs/sdks/taxassociations/README.md#update_tax_association) - Update tax association
* [delete_tax_association](docs/sdks/taxassociations/README.md#delete_tax_association) - Delete tax association

### [TaxRates](docs/sdks/taxrates/README.md)

* [get_tax_rates](docs/sdks/taxrates/README.md#get_tax_rates) - Get tax rates
* [create_tax_rate](docs/sdks/taxrates/README.md#create_tax_rate) - Create a tax rate
* [get_tax_rate](docs/sdks/taxrates/README.md#get_tax_rate) - Get a tax rate
* [update_tax_rate](docs/sdks/taxrates/README.md#update_tax_rate) - Update a tax rate
* [delete_tax_rate](docs/sdks/taxrates/README.md#delete_tax_rate) - Delete a tax rate

### [Tenants](docs/sdks/tenants/README.md)

* [get_tenant_billing_usage](docs/sdks/tenants/README.md#get_tenant_billing_usage) - Get billing usage for the current tenant
* [create_tenant](docs/sdks/tenants/README.md#create_tenant) - Create a new tenant
* [update_tenant](docs/sdks/tenants/README.md#update_tenant) - Update a tenant
* [get_tenant](docs/sdks/tenants/README.md#get_tenant) - Get tenant

### [Users](docs/sdks/users/README.md)

* [create_user](docs/sdks/users/README.md#create_user) - Create service account
* [get_user_info](docs/sdks/users/README.md#get_user_info) - Get current user
* [query_user](docs/sdks/users/README.md#query_user) - Query users

### [Wallets](docs/sdks/wallets/README.md)

* [get_customer_wallets](docs/sdks/wallets/README.md#get_customer_wallets) - Get Customer Wallets
* [get_wallets_by_customer_id](docs/sdks/wallets/README.md#get_wallets_by_customer_id) - Get wallets by customer ID
* [create_wallet](docs/sdks/wallets/README.md#create_wallet) - Create a new wallet
* [query_wallet](docs/sdks/wallets/README.md#query_wallet) - Query wallets
* [query_wallet_transaction](docs/sdks/wallets/README.md#query_wallet_transaction) - Query wallet transactions
* [get_wallet](docs/sdks/wallets/README.md#get_wallet) - Get wallet
* [update_wallet](docs/sdks/wallets/README.md#update_wallet) - Update a wallet
* [get_wallet_balance](docs/sdks/wallets/README.md#get_wallet_balance) - Get wallet balance
* [terminate_wallet](docs/sdks/wallets/README.md#terminate_wallet) - Terminate a wallet
* [top_up_wallet](docs/sdks/wallets/README.md#top_up_wallet) - Top up wallet
* [get_wallet_transactions](docs/sdks/wallets/README.md#get_wallet_transactions) - Get wallet transactions

### [Webhooks](docs/sdks/webhooks/README.md)

* [handle_chargebee_webhook](docs/sdks/webhooks/README.md#handle_chargebee_webhook) - Handle Chargebee webhook events
* [handle_hubspot_webhook](docs/sdks/webhooks/README.md#handle_hubspot_webhook) - Handle HubSpot webhook events
* [handle_moyasar_webhook](docs/sdks/webhooks/README.md#handle_moyasar_webhook) - Handle Moyasar webhook events
* [handle_nomod_webhook](docs/sdks/webhooks/README.md#handle_nomod_webhook) - Handle Nomod webhook events
* [handle_quickbooks_webhook](docs/sdks/webhooks/README.md#handle_quickbooks_webhook) - Handle QuickBooks webhook events
* [handle_razorpay_webhook](docs/sdks/webhooks/README.md#handle_razorpay_webhook) - Handle Razorpay webhook events
* [handle_stripe_webhook](docs/sdks/webhooks/README.md#handle_stripe_webhook) - Handle Stripe webhook events

### [Workflows](docs/sdks/workflows/README.md)

* [query_workflow](docs/sdks/workflows/README.md#query_workflow) - Query workflows

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `RetryConfig` object to the call:
```python
from flexprice_py import Flexprice
from flexprice_py.utils import BackoffStrategy, RetryConfig


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance",
        RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

    # Handle response
    print(res)

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `retry_config` optional parameter when initializing the SDK:
```python
from flexprice_py import Flexprice
from flexprice_py.utils import BackoffStrategy, RetryConfig


with Flexprice(
    server_url="https://api.example.com",
    retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:

    res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance")

    # Handle response
    print(res)

```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`FlexpriceError`](./src/flexprice_py/errors/flexpriceerror.py) is the base class for all HTTP error responses. It has the following properties:

| Property           | Type             | Description                                                                             |
| ------------------ | ---------------- | --------------------------------------------------------------------------------------- |
| `err.message`      | `str`            | Error message                                                                           |
| `err.status_code`  | `int`            | HTTP response status code eg `404`                                                      |
| `err.headers`      | `httpx.Headers`  | HTTP response headers                                                                   |
| `err.body`         | `str`            | HTTP body. Can be empty string if no body is returned.                                  |
| `err.raw_response` | `httpx.Response` | Raw HTTP response                                                                       |
| `err.data`         |                  | Optional. Some errors may contain structured data. [See Error Classes](#error-classes). |

### Example
```python
from flexprice_py import Flexprice, errors


with Flexprice(
    server_url="https://api.example.com",
    api_key_auth="<YOUR_API_KEY_HERE>",
) as flexprice:
    res = None
    try:

        res = flexprice.addons.create_addon(lookup_key="<value>", name="<value>", type_="multiple_instance")

        # Handle response
        print(res)


    except errors.FlexpriceError as e:
        # The base class for HTTP error responses
        print(e.message)
        print(e.status_code)
        print(e.body)
        print(e.headers)
        print(e.raw_response)

        # Depending on the method different errors may be thrown
        if isinstance(e, errors.ErrorsErrorResponse):
            print(e.data.error)  # Optional[models.ErrorsErrorDetail]
            print(e.data.success)  # Optional[bool]
```

### Error Classes
**Primary errors:**
* [`FlexpriceError`](./src/flexprice_py/errors/flexpriceerror.py): The base class for HTTP error responses.
  * [`ErrorsErrorResponse`](./src/flexprice_py/errors/errorserrorresponse.py): *

<details><summary>Less common errors (5)</summary>

<br />

**Network errors:**
* [`httpx.RequestError`](https://www.python-httpx.org/exceptions/#httpx.RequestError): Base class for request errors.
    * [`httpx.ConnectError`](https://www.python-httpx.org/exceptions/#httpx.ConnectError): HTTP client was unable to make a request to a server.
    * [`httpx.TimeoutException`](https://www.python-httpx.org/exceptions/#httpx.TimeoutException): HTTP request timed out.


**Inherit from [`FlexpriceError`](./src/flexprice_py/errors/flexpriceerror.py)**:
* [`ResponseValidationError`](./src/flexprice_py/errors/responsevalidationerror.py): Type mismatch between the response data and the expected Pydantic model. Provides access to the Pydantic validation error via the `cause` attribute.

</details>

\* Check [the method documentation](#available-resources-and-operations) to see if the error is applicable.
<!-- End Error Handling [errors] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Python SDK makes API calls using the [httpx](https://www.python-httpx.org/) HTTP library.  In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance.
Depending on whether you are using the sync or async version of the SDK, you can pass an instance of `HttpClient` or `AsyncHttpClient` respectively, which are Protocol's ensuring that the client has the necessary methods to make API calls.
This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of `httpx.Client` or `httpx.AsyncClient` directly.

For example, you could specify a header for every request that this sdk makes as follows:
```python
from flexprice_py import Flexprice
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = Flexprice(client=http_client)
```

or you could wrap the client with your own custom logic:
```python
from flexprice_py import Flexprice
from flexprice_py.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
    client: AsyncHttpClient

    def __init__(self, client: AsyncHttpClient):
        self.client = client

    async def send(
        self,
        request: httpx.Request,
        *,
        stream: bool = False,
        auth: Union[
            httpx._types.AuthTypes, httpx._client.UseClientDefault, None
        ] = httpx.USE_CLIENT_DEFAULT,
        follow_redirects: Union[
            bool, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
    ) -> httpx.Response:
        request.headers["Client-Level-Header"] = "added by client"

        return await self.client.send(
            request, stream=stream, auth=auth, follow_redirects=follow_redirects
        )

    def build_request(
        self,
        method: str,
        url: httpx._types.URLTypes,
        *,
        content: Optional[httpx._types.RequestContent] = None,
        data: Optional[httpx._types.RequestData] = None,
        files: Optional[httpx._types.RequestFiles] = None,
        json: Optional[Any] = None,
        params: Optional[httpx._types.QueryParamTypes] = None,
        headers: Optional[httpx._types.HeaderTypes] = None,
        cookies: Optional[httpx._types.CookieTypes] = None,
        timeout: Union[
            httpx._types.TimeoutTypes, httpx._client.UseClientDefault
        ] = httpx.USE_CLIENT_DEFAULT,
        extensions: Optional[httpx._types.RequestExtensions] = None,
    ) -> httpx.Request:
        return self.client.build_request(
            method,
            url,
            content=content,
            data=data,
            files=files,
            json=json,
            params=params,
            headers=headers,
            cookies=cookies,
            timeout=timeout,
            extensions=extensions,
        )

s = Flexprice(async_client=CustomClient(httpx.AsyncClient()))
```
<!-- End Custom HTTP Client [http-client] -->

<!-- Start Resource Management [resource-management] -->
## Resource Management

The `Flexprice` class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a [context manager][context-manager] and reuse it across the application.

[context-manager]: https://docs.python.org/3/reference/datamodel.html#context-managers

```python
from flexprice_py import Flexprice
def main():

    with Flexprice(
        server_url="https://api.example.com",
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as flexprice:
        # Rest of application here...


# Or when using async:
async def amain():

    async with Flexprice(
        server_url="https://api.example.com",
        api_key_auth="<YOUR_API_KEY_HERE>",
    ) as flexprice:
        # Rest of application here...
```
<!-- End Resource Management [resource-management] -->

<!-- Start Debugging [debug] -->
## Debugging

You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.
```python
from flexprice_py import Flexprice
import logging

logging.basicConfig(level=logging.DEBUG)
s = Flexprice(server_url="https://example.com", debug_logger=logging.getLogger("flexprice_py"))
```
<!-- End Debugging [debug] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=flexprice-py&utm_campaign=python)
