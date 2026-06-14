# WooCommerce GraphQL

WooCommerce provides GraphQL support via the **WPGraphQL WooCommerce** extension (also known as **WooGraphQL**). This is an open-source WordPress plugin that exposes WooCommerce store data through a GraphQL API powered by WPGraphQL.

## Source

- GitHub: https://github.com/wp-graphql/wp-graphql-woocommerce
- WPGraphQL: https://www.wpgraphql.com/
- WPGraphQL WooCommerce Docs: https://woographql.com/

## Endpoint

When WPGraphQL and WPGraphQL WooCommerce are installed on a WordPress/WooCommerce site, the GraphQL endpoint is available at:

```
https://yoursite.com/graphql
```

The endpoint supports both queries and mutations via HTTP POST with a JSON body containing `query` and optional `variables`.

## Authentication

- **Public queries**: Product listings, categories, and other catalog data are publicly accessible.
- **Customer session**: Cart and checkout operations use a session token (`woocommerce-session`) passed as an HTTP header.
- **Authenticated mutations**: Customer account mutations, order queries, and checkout require a WPGraphQL auth token (JWT) via the `Authorization: Bearer <token>` header.

## Schema Overview

The WPGraphQL WooCommerce schema covers the full WooCommerce data model including:

### Products
- `Product` (interface) — base fields shared by all product types
- `SimpleProduct` — single purchasable product
- `VariableProduct` — product with multiple variations
- `ExternalProduct` — affiliate/external product
- `GroupedProduct` — group of related simple products
- `ProductVariation` — a specific purchasable variant of a variable product
- `ProductCategory` — hierarchical product taxonomy
- `ProductTag` — product tag taxonomy
- `ProductAttribute` — product attribute (e.g., size, color)
- `GlobalProductAttribute` — site-wide reusable attribute
- `LocalProductAttribute` — product-specific attribute
- `ProductAttributeOption` — an option within an attribute (e.g., "Red", "Large")

### Media & Pricing
- `MediaItem` — WordPress media object used for product images
- `Gallery` — collection of product gallery images
- `PricingRange` — min/max price for variable products

### Inventory
- `StockStatus` (enum) — IN_STOCK, OUT_OF_STOCK, ON_BACKORDER
- `BackordersAllowed` (enum) — NO, NOTIFY, YES
- `ManageStock` (enum) — stock management mode
- `CatalogVisibility` (enum) — CATALOG, SEARCH, HIDDEN, VISIBLE

### Cart
- `Cart` — the current shopping cart
- `CartItem` — a product line in the cart
- `CartFee` — an additional fee applied to the cart
- `CartTax` — tax applied to the cart
- `CartContents` — collection of cart items
- `AppliedCoupon` — a coupon applied to the cart

### Coupons
- `Coupon` — discount coupon with type, amount, restrictions, and usage data

### Orders
- `Order` — a WooCommerce order
- `OrderItem` (interface) — base order line item
- `LineItem` — product line item in an order
- `ShippingLine` — shipping method applied to an order
- `TaxLine` — tax applied to an order
- `FeeLine` — additional fee on an order
- `OrderStatus` (enum) — PENDING, PROCESSING, ON_HOLD, COMPLETED, CANCELLED, REFUNDED, FAILED
- `MetaData` — arbitrary key-value metadata on orders, products, and customers

### Shipping
- `ShippingZone` — geographic zone for shipping rules
- `ShippingMethod` — a method available within a shipping zone
- `ShippingRate` — a calculated rate for a shipping method

### Tax
- `TaxRate` — a tax rate definition
- `TaxClass` — a tax classification (standard, reduced, zero)

### Customers
- `Customer` — a registered WooCommerce customer
- `CustomerAddress` — billing or shipping address for a customer

### Refunds
- `Refund` — a refund issued against an order
- `RefundedItem` — an individual refunded line item

### Reviews
- `Review` — a WooCommerce product review
- `ProductReview` — alias/extension of Review with product context

### Payments
- `PaymentGateway` — an available payment gateway (Stripe, PayPal, etc.)

### Checkout
- `Checkout` — checkout session state and available options

### Downloads
- `DownloadableFile` — a file associated with a downloadable product
- `DownloadableItem` — a downloadable item granted to a customer after purchase

### Subscriptions (WooCommerce Subscriptions extension)
- `Subscription` — a recurring billing subscription
- `SubscriptionItem` — a product line within a subscription

### Memberships (WooCommerce Memberships extension)
- `Membership` — a customer membership record
- `MembershipPlan` — a defined membership plan

### Session & Security
- `Session` — current user/guest session state
- `Nonce` — a WordPress nonce for form security

### Root Mutations
- `addToCart` — add a product to the cart
- `updateCartItem` — change quantity of a cart item
- `removeItemsFromCart` — remove items from the cart
- `applyCoupon` — apply a coupon code to the cart
- `removeCoupons` — remove coupons from the cart
- `checkout` — finalize the cart and create an order
- `login` — authenticate a customer and return a session token
- `registerCustomer` — create a new customer account
- `updateCustomer` — update customer profile and addresses
- `createOrder` — create an order programmatically (admin)
- `updateOrder` — update an existing order
- `deleteOrder` — delete an order
- `createRefund` — issue a refund against an order
- `writeReview` — submit a product review
- `deleteReview` — delete a product review
- `refreshJwtAuthToken` — refresh an expired auth token
- `sendPasswordResetEmail` — send a password reset email

## Example Queries

### Fetch Products
```graphql
query GetProducts {
  products(first: 10) {
    nodes {
      databaseId
      name
      slug
      type
      ... on SimpleProduct {
        price
        regularPrice
        salePrice
        stockStatus
      }
      ... on VariableProduct {
        price
        variations {
          nodes {
            databaseId
            name
            price
            stockStatus
          }
        }
      }
      image {
        sourceUrl
        altText
      }
      productCategories {
        nodes {
          name
          slug
        }
      }
    }
  }
}
```

### Fetch Cart
```graphql
query GetCart {
  cart {
    subtotal
    total
    totalTax
    shippingTotal
    contents {
      nodes {
        key
        quantity
        total
        product {
          node {
            name
            slug
          }
        }
      }
    }
    appliedCoupons {
      code
      discountAmount
    }
  }
}
```

### Add to Cart
```graphql
mutation AddToCart($productId: Int!, $quantity: Int!) {
  addToCart(input: { productId: $productId, quantity: $quantity }) {
    cart {
      total
      contents {
        itemCount
      }
    }
    cartItem {
      key
      quantity
    }
  }
}
```

### Checkout
```graphql
mutation Checkout($input: CheckoutInput!) {
  checkout(input: $input) {
    order {
      databaseId
      orderNumber
      status
      total
    }
    result
    redirect
  }
}
```

## Resources

- WPGraphQL WooCommerce GitHub: https://github.com/wp-graphql/wp-graphql-woocommerce
- WooGraphQL Documentation: https://woographql.com/docs
- WPGraphQL Documentation: https://www.wpgraphql.com/docs
- WooCommerce Developer Docs: https://developer.woocommerce.com/docs/
