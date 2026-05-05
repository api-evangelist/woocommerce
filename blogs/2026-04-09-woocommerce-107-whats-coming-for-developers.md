---
title: "WooCommerce 10.7: What’s coming for developers"
url: "https://developer.woocommerce.com/2026/04/09/woocommerce-10-7-whats-coming-for-developers/"
date: "Thu, 09 Apr 2026 13:51:15 +0000"
author: "Shani Banerjee"
feed_url: "https://developer.woocommerce.com/feed/"
---
<div class="wp-block-group alignwide has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-ea8e1d93 wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>WooCommerce 10.7 is coming soon&#8230;</strong></p>



<p>The post will track the work we do as we prepare to release 10.7 as well as provide a preview of what&#8217;s to come in this new version.</p>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<p class="has-small-font-size" style="margin-top: 0; margin-bottom: 0; padding-top: 0; padding-bottom: 0;"><strong>Release Schedule:</strong></p>



<ul class="wp-block-list has-small-font-size">
<li><img alt="🧪" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f9ea.png" style="height: 1em;" /> <a href="https://github.com/woocommerce/woocommerce/releases/tag/10.7.0-beta.2">WooCommerce 10.7 beta2</a> is available for testing</li>
</ul>



<ul class="wp-block-list" style="margin-top: 0; margin-bottom: 0;">
<li class="has-small-font-size">Final Release — <strong>April 14, 2026</strong></li>



<li class="has-small-font-size"><a href="#h-update-timeline">See updates</a></li>
</ul>
</div>
</div>
</div>
</div>



<p>Hey folks, on Monday, March 30, 2026, we kicked off our Feature Freeze ahead of the release of WooCommerce 10.7. As we begin the testing phase and get the release ready, we wanted to share some spoilers and document any updates to the expected release timeline.</p>



<p><strong>Check back here for more updates ahead of the WooCommerce 10.7 release</strong>, scheduled for <strong>Tuesday, April 14, 2026</strong>.</p>



<span id="more-8769907"></span>



<h2 class="wp-block-heading" id="h-what-s-coming-in-10-7">What&#8217;s coming in 10.7</h2>



<h3 class="wp-block-heading" id="h-performance-optimizations-continue-to-deliver-measurable-improvements">Performance optimizations continue to deliver measurable improvements</h3>



<p>This release includes some of the most significant query reduction work in recent memory. HPOS order queries on <code>/wc/v4/orders</code> drop from 271 to 132 through cache priming that eliminates N+1 queries during REST API serialization <a href="https://github.com/woocommerce/woocommerce/pull/63440">#63440</a>, and checkout flows see around a 15% reduction in total SQL queries <a href="https://github.com/woocommerce/woocommerce/pull/63258">#63258</a>.</p>



<p>Cache priming is now applied consistently across product grids, linked products, and orders. New database indexes on <code>woocommerce_shipping_zone_methods</code> speed up zone lookups <a href="https://github.com/woocommerce/woocommerce/pull/63674">#63674</a>, and the Store API products endpoint now caches the <code>Last-Modified</code> timestamp to skip a database query on cache hits <a href="https://github.com/woocommerce/woocommerce/pull/63228">#63228</a>. A new <code>woocommerce_pre_refresh_order_count_cache</code> filter lets you opt out of redundant order count refreshes in high-traffic scenarios <a href="https://github.com/woocommerce/woocommerce/pull/63747">#63747</a>.</p>



<h3 class="wp-block-heading" id="h-order-fulfillments-gets-a-proper-api-beta">Order fulfillments gets a proper API <em>(Beta)</em></h3>



<p>The fulfillments system receives its most significant update yet. Note that this feature is still in beta. Custom shipping providers are now supported via a new <code>wc_fulfillment_shipping_provider</code> taxonomy, accessible through a new Settings page at Shipping &gt; Shipping Providers <a href="https://github.com/woocommerce/woocommerce/pull/63766">#63766</a>.</p>



<p>The PHP API now exposes typed methods including <code>get_tracking_number()</code>, <code>set_tracking_number()</code>, and <code>get_shipping_provider()</code> <a href="https://github.com/woocommerce/woocommerce/pull/63573">#63573</a>. Fulfillment lifecycle events are now automatically logged as order notes via a new <code>FULFILLMENT</code> order note group constant <a href="https://github.com/woocommerce/woocommerce/pull/63516">#63516</a>. The data store is now registered via <code>woocommerce_data_stores</code>, so extensions can swap in a custom implementation <a href="https://github.com/woocommerce/woocommerce/pull/63485">#63485</a>.</p>



<h3 class="wp-block-heading" id="h-store-api-additions">Store API additions</h3>



<p>Products in the Store API now return <code>weight</code>, <code>dimensions</code>, <code>formatted_weight</code>, and <code>formatted_dimensions</code> fields, giving frontend applications access to full product specifications in a single request.</p>



<p>Upsells, cross-sells, and related products are now available as embeddable <code>_links</code> with <code>embeddable: true</code>, meaning a single <code>?_embed</code> request can pull in all related product data without additional calls <a href="https://github.com/woocommerce/woocommerce/pull/62603">#62603</a>. A new <code>?related=ID</code> query parameter enables filtering products by relationship. Draft and unpublished products now correctly return 404 on Store API single routes <a href="https://github.com/woocommerce/woocommerce/pull/63466">#63466</a>, and thumbnail <code>srcset</code> and <code>sizes</code> fixes ensure the right image is served in cart contexts <a href="https://github.com/woocommerce/woocommerce/pull/63731">#63731</a>.</p>



<h3 class="wp-block-heading" id="h-cart-and-checkout-block-refinements">Cart and Checkout block refinements</h3>



<p>The cart store now fetches a fresh nonce on load and awaits it before any POST operations, fixing 403 errors that would surface on cached pages <a href="https://github.com/woocommerce/woocommerce/pull/62892">#62892</a>. Password-protected product descriptions are now redacted in Store API responses <a href="https://github.com/woocommerce/woocommerce/pull/63466">#63466</a>, and payment method radio buttons are always shown even when only a single option is available <a href="https://github.com/woocommerce/woocommerce/pull/63351">#63351</a>. Color inheritance fixes also improve form styling consistency in dark mode themes.</p>



<h3 class="wp-block-heading" id="h-analytics-export-filters">Analytics export filters</h3>



<p>New <code>woocommerce_report_{type}_export_columns</code> and <code>woocommerce_report_{type}_prepare_export_item</code> filters are now available for Revenue Stats, Taxes, and Variations exports. Currency and custom filter parameters are now correctly forwarded to background export jobs <a href="https://github.com/woocommerce/woocommerce/pull/63618">#63618</a>, which is particularly useful if you&#8217;re building multicurrency tooling on top of WooCommerce analytics.</p>



<h3 class="wp-block-heading" id="h-experimental-block-based-email-editor-improvements">Experimental block-based email editor improvements</h3>



<p>Work on the <a href="https://github.com/woocommerce/woocommerce/tree/trunk/packages/php/email-editor">block-based email editor</a> continues to move forward. This release lays the groundwork for <code>alignfull</code> block support, allowing blocks to eventually span the full email width <a href="https://github.com/woocommerce/woocommerce/pull/63752">#63752</a>. WordPress embed cards now display featured images, titles, and excerpts rather than plain links <a href="https://github.com/woocommerce/woocommerce/pull/63542">#63542</a>, and template management gains a &#8220;Reset to default&#8221; action.</p>



<p>Two new filters add extensibility: <code>woocommerce_email_block_template_html</code> for customizing reset template content <a href="https://github.com/woocommerce/woocommerce/pull/63558">#63558</a>, and <code>woocommerce_email_editor_send_button_disabled</code> for enabling auto-save workflows before send <a href="https://github.com/woocommerce/woocommerce/pull/63722">#63722</a>. Note that the email editor remains behind a feature flag in Woo core.</p>



<h2 class="wp-block-heading" id="h-developer-advisories">Developer advisories</h2>



<p><strong>Fulfillments namespace has changed</strong>: The namespace has moved from <code>Automattic\WooCommerce\Internal\Fulfillments</code> to <code>Automattic\WooCommerce\Admin\Features\Fulfillments</code>. If your extension references the old path directly, you&#8217;ll need to update it before 10.7.</p>



<p><strong>Security hardening across several surfaces</strong>: XSS protection via <code>wp_kses_post()</code> has been extended to the v4 REST API order notes endpoint, matching the protection already in place for v1 through v3 <a href="https://github.com/woocommerce/woocommerce/pull/63661">#63661</a>. CSRF validation has been added to product and term ordering AJAX handlers <a href="https://github.com/woocommerce/woocommerce/pull/63422">#63422</a>. Payment gateway password fields no longer corrupt values containing <code>%</code> characters <a href="https://github.com/woocommerce/woocommerce/pull/63597">#63597</a>.</p>



<h2 class="wp-block-heading" id="h-changelog">Changelog</h2>



<p>View the full <a href="https://github.com/woocommerce/woocommerce/blob/trunk/plugins/woocommerce/readme.txt">changelog</a>.</p>



<h2 class="wp-block-heading" id="h-update-timeline">Update timeline</h2>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<p><img alt="✅" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/2705.png" style="height: 1em;" /> <strong>Feature Freeze</strong></p>



<p class="has-small-font-size"><em>Added: March 30, 2026</em></p>



<p><img alt="✅" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/2705.png" style="height: 1em;" /> <strong>WooCommerce 10.7 Beta 1</strong></p>



<p class="has-small-font-size"><em>Released: March 30, 2026</em></p>



<p><img alt="✅" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/2705.png" style="height: 1em;" /> <strong>WooCommerce 10.7 Beta 2</strong></p>



<p class="has-small-font-size"><em>Released: April 7, 2026</em></p>



<p><img alt="⏳" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/23f3.png" style="height: 1em;" /> <strong>WooCommerce 10.7 RC 1</strong></p>



<p class="has-small-font-size"><em>Scheduled: April 13, 2026. <img alt="👉" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f449.png" style="height: 1em;" /> <strong>To Test:</strong> Use the <a href="https://woocommerce.com/products/woocommerce-beta-tester/">WooCommerce Beta Tester plugin</a> to try RC versions.</em></p>



<p><img alt="⏳" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/23f3.png" style="height: 1em;" /> <strong>WooCommerce Release 10.7</strong></p>



<p class="has-small-font-size"><em>Scheduled: April 14, 2026</em></p>
</div>



<p></p>
<p>The post <a href="https://developer.woocommerce.com/2026/04/09/woocommerce-10-7-whats-coming-for-developers/">WooCommerce 10.7: What&#8217;s coming for developers</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
