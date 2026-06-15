# WooCommerce (woocommerce)

WooCommerce is the world's most popular open-source eCommerce platform, built on WordPress. It provides a comprehensive REST API for managing products, orders, customers, coupons, reports, webhooks, and store settings, plus a public-facing Store API for headless frontends. WooCommerce also delivers real-time events via webhooks for order, product, customer, and subscription lifecycle changes.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/woocommerce/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/woocommerce/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- eCommerce
- Open Source
- Orders
- Products
- WordPress

## Timestamps

- **Created:** 2026-05-03
- **Modified:** 2026-05-19

## APIs

### WooCommerce REST API

The WooCommerce REST API is the primary server-side interface for reading and writing WooCommerce store data programmatically. It follows REST conventions, uses JSON, and is integrated with the WordPress REST API under /wp-json/wc/v3/. The API covers products, variations, categories, attributes, orders, customers, coupons, tax rates, shipping zones, payment gateways, settings, webhooks, reports, and system status. Authentication uses Consumer Key and Consumer Secret pairs via HTTP Basic Auth or OAuth 1.0a.

- **Human URL:** [https://developer.woocommerce.com/docs/apis/rest-api/](https://developer.woocommerce.com/docs/apis/rest-api/)
- **Base URL:** `https://example.com/wp-json/wc/v3`

#### Tags

- eCommerce
- Orders
- Products
- REST

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/rest-api/)
- [API Reference](https://woocommerce.github.io/woocommerce-rest-api-docs/)
- [Authentication](https://woocommerce.github.io/woocommerce-rest-api-docs/#authentication)
- [OpenAPI](openapi/woocommerce-rest-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/woocommerce-rest-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/woocommerce-rest-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/woocommerce-rest-api-order-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/woocommerce-rest-api-product-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/woocommerce-rest-api-customer-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/woocommerce-rest-api-coupon-schema.json) — [JSON Schema](https://json-schema.org/specification)

### WooCommerce Store API

The WooCommerce Store API provides unauthenticated public REST endpoints for building customer-facing cart, checkout, and product functionality. Accessible under /wp-json/wc/store/v1/, it covers products, categories, attributes, tags, reviews, cart operations, checkout, and customer orders. Write operations require a nonce token from the cart response.

- **Human URL:** [https://developer.woocommerce.com/docs/apis/store-api/](https://developer.woocommerce.com/docs/apis/store-api/)
- **Base URL:** `https://example.com/wp-json/wc/store/v1`

#### Tags

- Cart
- Checkout
- eCommerce
- Headless
- Products

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/store-api/)
- [OpenAPI](openapi/woocommerce-store-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/woocommerce-store-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/woocommerce-store-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/woocommerce-store-api-cart-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/woocommerce-store-api-store-product-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/woocommerce-store-api-checkout-schema.json) — [JSON Schema](https://json-schema.org/specification)

### WooCommerce Webhook Events

WooCommerce delivers real-time event notifications via HTTP POST webhooks for orders, products, customers, coupons, and subscriptions lifecycle changes. Webhooks are configured in the WooCommerce admin or via the REST API and deliver JSON payloads signed with HMAC-SHA256.

- **Human URL:** [https://woocommerce.com/document/webhooks/](https://woocommerce.com/document/webhooks/)

#### Tags

- Events
- Webhooks

#### Properties

- [Documentation](https://woocommerce.com/document/webhooks/)
- [AsyncAPI](asyncapi/woocommerce-webhooks-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [JSON Schema](json-schema/woocommerce-rest-api-webhook-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [Postman Collection](collections/woocommerce-rest-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/woocommerce-rest-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/woocommerce-store-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/woocommerce-store-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [LinkedIn](https://www.linkedin.com/company/woocommerce)
- [Website](https://woocommerce.com)
- [Developer Portal](https://developer.woocommerce.com)
- [Documentation](https://developer.woocommerce.com/docs/)
- [Getting Started](https://developer.woocommerce.com/docs/getting-started/)
- [Git Hub](https://github.com/woocommerce/woocommerce)
- [GitHub Organization](https://github.com/woocommerce)
- [Blog](https://developer.woocommerce.com/blog/)
- [Support](https://woocommerce.com/support/)
- [Forum](https://wordpress.org/support/plugin/woocommerce/)
- [Release Notes](https://developer.woocommerce.com/changelog/)
- [Status Page](https://status.woocommerce.com)
- [JSON-LD](json-ld/woocommerce-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Spectral Rules](rules/woocommerce-spectral-rules.yml)
- [Vocabulary](vocabulary/woocommerce-vocabulary.yaml)
- [Tools](https://github.com/woocommerce/woocommerce-rest-api-js-lib)
- [Tools](https://github.com/woocommerce/wc-api-php)
- [Tools](https://github.com/woocommerce/qit-mcp)
- [Tools](https://github.com/woocommerce/wc-mcp-ability)
- [SDK](https://www.npmjs.com/package/@woocommerce/woocommerce-rest-api)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)
- [M C P Server](https://github.com/woocommerce/wc-mcp-ability)
- [L L Ms Txt](https://developer.woocommerce.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
