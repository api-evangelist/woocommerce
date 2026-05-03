# WooCommerce (woocommerce)
WooCommerce is the world's most popular open-source eCommerce platform, built on WordPress. It provides a comprehensive REST API for managing products, orders, customers, coupons, reports, webhooks, and store settings, plus a public-facing Store API for headless frontends. WooCommerce also delivers real-time events via webhooks for order, product, customer, and subscription lifecycle changes.

**URL:** [https://woocommerce.com](https://woocommerce.com)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - eCommerce, Open Source, Orders, Products, WordPress

## Timestamps

- **Created:** 2026-05-03
- **Modified:** 2026-05-03

## APIs

### WooCommerce REST API
The WooCommerce REST API is the primary server-side interface for reading and writing WooCommerce store data programmatically. It follows REST conventions, uses JSON, and is integrated with the WordPress REST API under /wp-json/wc/v3/. The API covers products, variations, categories, attributes, orders, customers, coupons, tax rates, shipping zones, payment gateways, settings, webhooks, reports, and system status. Authentication uses Consumer Key and Consumer Secret pairs via HTTP Basic Auth or OAuth 1.0a.

**Human URL:** [https://developer.woocommerce.com/docs/apis/rest-api/](https://developer.woocommerce.com/docs/apis/rest-api/)

#### Tags:

 - eCommerce, Orders, Products, REST

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/rest-api/)
- [API Reference](https://woocommerce.github.io/woocommerce-rest-api-docs/)
- [Authentication](https://woocommerce.github.io/woocommerce-rest-api-docs/#authentication)
- [OpenAPI](openapi/woocommerce-rest-api-openapi.yml)
- [Order Schema](json-schema/woocommerce-rest-api-order-schema.json)
- [Product Schema](json-schema/woocommerce-rest-api-product-schema.json)
- [Customer Schema](json-schema/woocommerce-rest-api-customer-schema.json)
- [Coupon Schema](json-schema/woocommerce-rest-api-coupon-schema.json)

### WooCommerce Store API
The WooCommerce Store API provides unauthenticated public REST endpoints for building customer-facing cart, checkout, and product functionality. Accessible under /wp-json/wc/store/v1/, it covers products, categories, attributes, tags, reviews, cart operations, checkout, and customer orders. Write operations require a nonce token from the cart response.

**Human URL:** [https://developer.woocommerce.com/docs/apis/store-api/](https://developer.woocommerce.com/docs/apis/store-api/)

#### Tags:

 - Cart, Checkout, eCommerce, Headless, Products

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/store-api/)
- [OpenAPI](openapi/woocommerce-store-api-openapi.yml)
- [Cart Schema](json-schema/woocommerce-store-api-cart-schema.json)
- [Store Product Schema](json-schema/woocommerce-store-api-store-product-schema.json)
- [Checkout Schema](json-schema/woocommerce-store-api-checkout-schema.json)

### WooCommerce Webhook Events
WooCommerce delivers real-time event notifications via HTTP POST webhooks for orders, products, customers, coupons, and subscriptions lifecycle changes. Webhooks are configured in the WooCommerce admin or via the REST API and deliver JSON payloads signed with HMAC-SHA256.

**Human URL:** [https://woocommerce.com/document/webhooks/](https://woocommerce.com/document/webhooks/)

#### Tags:

 - Events, Webhooks

#### Properties

- [Documentation](https://woocommerce.com/document/webhooks/)
- [AsyncAPI](asyncapi/woocommerce-webhooks-asyncapi.yml)
- [Webhook Schema](json-schema/woocommerce-rest-api-webhook-schema.json)

## Common Properties

- [Website](https://woocommerce.com)
- [Developer Portal](https://developer.woocommerce.com)
- [Documentation](https://developer.woocommerce.com/docs/)
- [Getting Started](https://developer.woocommerce.com/docs/getting-started/)
- [GitHub](https://github.com/woocommerce/woocommerce)
- [GitHub Organization](https://github.com/woocommerce)
- [Blog](https://developer.woocommerce.com/blog/)
- [Support](https://woocommerce.com/support/)
- [Forum](https://wordpress.org/support/plugin/woocommerce/)
- [Release Notes](https://developer.woocommerce.com/changelog/)
- [Status Page](https://status.woocommerce.com)
- [JSON-LD Context](json-ld/woocommerce-context.jsonld)
- [Spectral Rules](rules/woocommerce-spectral-rules.yml)
- [WooCommerce REST API JavaScript Library](https://github.com/woocommerce/woocommerce-rest-api-js-lib)
- [WooCommerce REST API PHP Library](https://github.com/woocommerce/wc-api-php)
- [WooCommerce QIT MCP Server](https://github.com/woocommerce/qit-mcp)
- [WooCommerce MCP Ability Plugin](https://github.com/woocommerce/wc-mcp-ability)
- [WooCommerce REST API JS Library (npm)](https://www.npmjs.com/package/@woocommerce/woocommerce-rest-api)

## Features

| Name | Description |
|------|-------------|
| Product Management | Create and manage products, variations, categories, attributes, tags, and shipping classes. |
| Order Management | Full order lifecycle management including creation, updates, notes, and refunds. |
| Customer Management | Manage customer accounts with billing and shipping addresses. |
| Coupon System | Create and manage discount coupons with usage restrictions and expiry. |
| Webhook Events | Real-time HTTP POST notifications for store events including orders, products, and customers. |
| Headless Commerce | Store API provides unauthenticated endpoints for building custom frontends. |
| Payment Gateway API | Configure and manage payment gateways programmatically. |
| Shipping Zones API | Manage shipping zones, methods, and rates via the REST API. |

## Use Cases

| Name | Description |
|------|-------------|
| Headless Storefront | Build custom React or Vue frontends using the Store API for products, cart, and checkout. |
| ERP Integration | Sync orders and inventory with ERP systems via the REST API and webhooks. |
| Order Fulfillment | Automate order fulfillment workflows using webhook notifications and REST API updates. |
| Product Catalog Sync | Sync product catalog from a PIM system to WooCommerce via the REST API. |
| Analytics and Reporting | Pull sales reports and customer data via the Reports API for BI tools. |

## Integrations

| Name | Description |
|------|-------------|
| WordPress | WooCommerce runs as a WordPress plugin and uses the WordPress REST API infrastructure. |
| PayPal | Official PayPal payment gateway integration for WooCommerce. |
| Stripe | Official Stripe payment gateway integration. |
| ShipStation | Order fulfillment and shipping integration. |
| Mailchimp | Email marketing integration for customer segmentation and abandoned cart. |
| Reddit Ads | Official Reddit for WooCommerce integration for ad conversion tracking. |
| Pinterest | Official Pinterest for WooCommerce integration for product sync. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [WooCommerce REST API](openapi/woocommerce-rest-api-openapi.yml)
- [WooCommerce Store API](openapi/woocommerce-store-api-openapi.yml)

### AsyncAPI

- [WooCommerce Webhook Events](asyncapi/woocommerce-webhooks-asyncapi.yml)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [WooCommerce REST API](capabilities/shared/rest-api.yaml) — 10 operations for store management
- [WooCommerce Store API](capabilities/shared/store-api.yaml) — 7 operations for headless storefront

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Store Management](capabilities/store-management.yaml) | REST API, Store API | 13 | Store Administrator, Operations Manager |
| [Headless Commerce](capabilities/headless-commerce.yaml) | Store API, REST API | 8 | Frontend Developer, Headless Architect |

## Vocabulary

- [WooCommerce Vocabulary](vocabulary/woocommerce-vocabulary.yaml) — Unified taxonomy mapping 12 resources, 10 actions, 2 workflows, and 4 personas across operational (OpenAPI) and capability (Naftiko) dimensions

## Rules

- [WooCommerce Spectral Rules](rules/woocommerce-spectral-rules.yml) — Spectral ruleset enforcing WooCommerce API conventions

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
