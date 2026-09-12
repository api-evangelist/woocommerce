---
title: "Changes to order item deletion in WooCommerce 11.1"
url: "https://developer.woocommerce.com/2026/08/31/changes-to-order-item-deletion/"
date: "2026-08-31"
author: "Thomas Roberts"
feed_url: "https://developer.woocommerce.com/feed/"
---
11.0 added deferred deletion for order items, which clears memory items while DB deletion occurs. 11.1 enhances this so that only the IDs you specify get deleted. Custom stores can opt into delayed deletion by overriding a new method.
