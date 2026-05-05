---
title: "WooCommerce 10.6.1: Dot Release"
url: "https://developer.woocommerce.com/2026/03/12/woocommerce-10-6-1-dot-release/"
date: "Thu, 12 Mar 2026 19:29:58 +0000"
author: "Brian Coords"
feed_url: "https://developer.woocommerce.com/feed/"
---
<div class="wp-block-group alignwide has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-ea8e1d93 wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>WooCommerce 10.6.1 has been released</strong>.</p>



<p>WooCommerce 10.6.1 is a maintenance release fixing issues including attribute validation in the Add to Cart block, payment gateway ordering in settings, and shipping address field display.</p>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<div class="wp-block-group is-vertical is-layout-flex wp-container-core-group-is-layout-4b827052 wp-block-group-is-layout-flex">
<p><strong>Current Stable Tag </strong></p>



<p>
	<img alt="👉" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f449.png" style="height: 1em;" /> <a href="https://downloads.wordpress.org/plugin/woocommerce.10.6.2.zip"><strong>WooCommerce 10.6.2</strong></a>
</p>
</div>



<ul class="wp-block-list">
<li class="has-small-font-size">Released — March 12, 2026</li>
</ul>
</div>
</div>
</div>
</div>



<span id="more-8769873"></span>



<h2 class="wp-block-heading" id="h-what-s-in-this-release">What&#8217;s in this release</h2>



<p><strong>Fixed attribute options being incorrectly disabled</strong> in the Add to Cart with Options block for variable products whose attribute slugs contain hyphens. The issue occurred because PHP passes attribute names as slugs (e.g., <code>some-name</code>) while the Store API returns labels with spaces (e.g., <code>some name</code>), causing strict comparisons to fail. The fix updates <code>normalizeAttributeName()</code> to replace hyphens with spaces, ensuring consistent normalization across all comparison points. <a href="https://github.com/woocommerce/woocommerce/pull/63647">#63647</a></p>



<p><strong>Newly installed payment gateways now appear above offline payment methods</strong> instead of being placed at the bottom of the list. Previously, installed gateways were buried below others, preventing them from being expanded by default on checkout. The updated placement logic inserts new gateways above the offline payment group unless merchants have customized the ordering. <a href="https://github.com/woocommerce/woocommerce/pull/63648">#63648</a></p>



<p><strong>Shipping package titles in the shortcode now displays as &#8220;Shipment&#8221; instead of &#8220;Shipment 1&#8221;</strong> when only one package is present. The <code>get_shipping_package_name()</code> method now receives the total package count, allowing it to conditionally name single packages as &#8220;Shipment&#8221; while multiple packages continue to show numbered labels like &#8220;Shipment 1&#8221; and &#8220;Shipment 2&#8221;. <a href="https://github.com/woocommerce/woocommerce/pull/63649">#63649</a></p>



<p></p>
<p>The post <a href="https://developer.woocommerce.com/2026/03/12/woocommerce-10-6-1-dot-release/">WooCommerce 10.6.1: Dot Release</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
