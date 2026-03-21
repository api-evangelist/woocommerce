# WooCommerce (woocommerce)
WooCommerce is an open-source e-commerce platform built on WordPress that powers online stores of all sizes. It provides a comprehensive developer platform including REST APIs, a Store API for headless storefronts, webhook event delivery, and PHP extension frameworks for payments, shipping, and settings, enabling developers to build, extend, and integrate with WooCommerce-powered stores.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/woocommerce/refs/heads/main/apis.yml)

## Scope

- **Type:** Contract
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags:

 - E-Commerce, WordPress, Products, Orders, Payments, Shipping, Extensions

## Timestamps

- **Created:** 2026-03-21
- **Modified:** 2026-03-21

## APIs

### WooCommerce REST API
The WooCommerce REST API is the primary server-side interface for reading and writing WooCommerce store data programmatically. It follows REST conventions, uses JSON for all requests and responses, and is fully integrated with the WordPress REST API under the /wp-json/wc/v3/ namespace. The API covers a broad set of resources including products, product categories, product attributes, orders, order refunds, customers, coupons, tax rates, shipping zones, payment gateways, settings, reports, webhooks, and system status. Authentication is handled via API keys (Consumer Key and Consumer Secret) generated in the WooCommerce admin, sent over HTTPS using HTTP Basic Auth.

**Human URL:** [https://developer.woocommerce.com/docs/apis/rest-api/](https://developer.woocommerce.com/docs/apis/rest-api/)


#### Tags:

 - E-Commerce, WordPress, Products, Orders, Customers

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/rest-api/)
- [Documentation](https://woocommerce.github.io/woocommerce-rest-api-docs/)
- [OpenAPI](openapi/woocommerce-rest-api-openapi.yml)

### WooCommerce Store API
The WooCommerce Store API provides unauthenticated public REST endpoints for building customer-facing cart, checkout, and product functionality. Unlike the authenticated REST API, it is designed for frontend integrations and does not expose sensitive store data or other customers' information. The API is accessible under the /wp-json/wc/store/v1/ namespace and covers products, product categories, attributes, tags, reviews, cart operations, checkout, and current customer orders. It uses cookie-based sessions to scope cart and checkout state to the active shopper, making it well-suited for building headless storefronts and custom block-based checkout experiences.

**Human URL:** [https://developer.woocommerce.com/docs/apis/store-api/](https://developer.woocommerce.com/docs/apis/store-api/)


#### Tags:

 - E-Commerce, WordPress, Cart, Checkout, Storefront

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/apis/store-api/)
- [OpenAPI](openapi/woocommerce-store-api-openapi.yml)

### WooCommerce Webhooks
WooCommerce Webhooks deliver HTTP POST event notifications to a configured URL whenever specific store events occur. Supported topics include create, update, and delete actions for orders, products, coupons, and customers, as well as custom action-based topics such as woocommerce_add_to_cart. Webhooks are configured through the WooCommerce admin under Settings > Advanced > Webhooks, or managed programmatically via the REST API /webhooks endpoints. Each webhook includes a configurable secret key used to generate an HMAC signature in the request headers for payload verification. The system automatically disables a webhook after five consecutive delivery failures.

**Human URL:** [https://developer.woocommerce.com/docs/best-practices/urls-and-routing/webhooks/](https://developer.woocommerce.com/docs/best-practices/urls-and-routing/webhooks/)


#### Tags:

 - Webhooks, Events, Notifications, E-Commerce

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/best-practices/urls-and-routing/webhooks/)
- [Documentation](https://woocommerce.com/document/webhooks/)
- [AsyncAPI](asyncapi/woocommerce-webhooks-asyncapi.yml)
- [JSONSchema](json-schema/woocommerce-webhook-schema.json)

### WooCommerce Payment Gateway API
The WooCommerce Payment Gateway API is a PHP class-based framework for building custom payment method integrations as WordPress plugins. Developers extend the WC_Payment_Gateway base class to define payment form fields, handle checkout form submission, process payments with third-party processors, and update order statuses. The API supports multiple integration patterns including form-based, iframe-based, direct API calls, and offline payment methods. It integrates with the WooCommerce Settings API for gateway configuration and provides built-in order methods such as payment_complete() to ensure consistent stock and status management across all payment types.

**Human URL:** [https://developer.woocommerce.com/docs/features/payments/payment-gateway-api/](https://developer.woocommerce.com/docs/features/payments/payment-gateway-api/)


#### Tags:

 - Payments, PHP, WordPress, Extensions, E-Commerce

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/features/payments/payment-gateway-api/)

### WooCommerce Settings API
The WooCommerce Settings API is a PHP framework that enables plugin and extension developers to define, display, save, and load configuration settings within the WordPress admin interface. Developers extend the WC_Settings_API class and declare form fields covering input types such as text, textarea, checkbox, select, and multiselect. The API automatically generates the HTML output for the settings page, handles form submission via process_admin_options(), and persists values to the WordPress database. It is used by payment gateways, shipping methods, and other WooCommerce extensions to provide a standardized configuration experience without requiring custom settings infrastructure.

**Human URL:** [https://developer.woocommerce.com/docs/extensions/settings-and-config/settings-api/](https://developer.woocommerce.com/docs/extensions/settings-and-config/settings-api/)


#### Tags:

 - PHP, WordPress, Extensions, Configuration, Settings

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/extensions/settings-and-config/settings-api/)

### WooCommerce Shipping Method API
The WooCommerce Shipping Method API is a PHP class-based framework for creating custom shipping integrations as WordPress plugins. Developers extend the WC_Shipping_Method base class to define shipping rate calculation logic, configure method settings, and add rates to the cart based on package contents, destination, and other cart data. Custom shipping methods appear alongside built-in options such as flat rate and free shipping in the WooCommerce checkout. The API integrates with the Settings API for per-instance configuration and supports shipping zones, allowing merchants to apply different custom methods to different geographic regions.

**Human URL:** [https://developer.woocommerce.com/docs/features/shipping/shipping-method-api/](https://developer.woocommerce.com/docs/features/shipping/shipping-method-api/)


#### Tags:

 - Shipping, PHP, WordPress, Extensions, E-Commerce

#### Properties

- [Documentation](https://developer.woocommerce.com/docs/features/shipping/shipping-method-api/)

## Common Properties

- [Portal](https://developer.woocommerce.com/)
- [Documentation](https://developer.woocommerce.com/docs/)
- [Website](https://woocommerce.com/)
- [PrivacyPolicy](https://automattic.com/privacy/)
- [TermsOfService](https://woocommerce.com/terms-conditions/)
- [Support](https://developer.woocommerce.com/support/)
- [Blog](https://developer.woocommerce.com/blog/)
- [Login](https://woocommerce.com/my-account/)

## Maintainers

**FN:** API Evangelist

**Email:** info@apievangelist.com
