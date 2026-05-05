---
title: "WooCommerce 10.6: Enhanced blocks and a faster dashboard"
url: "https://developer.woocommerce.com/2026/03/10/woocommerce-10-6-enhanced-blocks-and-a-faster-dashboard/"
date: "Tue, 10 Mar 2026 21:10:38 +0000"
author: "Brian Coords"
feed_url: "https://developer.woocommerce.com/feed/"
---
<div class="wp-block-group alignwide has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-ea8e1d93 wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>WooCommerce 10.6</strong> has been released on <strong>March 10, 2026.</strong> This post highlights what&#8217;s new in this version of WooCommerce.</p>



<p class="has-small-font-size">See our <a href="https://docs.woocommerce.com/document/how-to-update-woocommerce/">update guide</a>.<br /><a href="https://wordpress.org/plugins/woocommerce/">Download directly</a> from WordPress.org.</p>



<div class="wp-block-group has-small-font-size has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<p><strong><strong>Other important information:</strong></strong></p>



<ul class="wp-block-list" style="margin-top: 0; margin-bottom: 0;">
<li><img alt="📀" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f4c0.png" style="height: 1em;" />  This release <strong>does</strong> include a <a href="#h-database-updates">database update</a>.</li>



<li><a href="#h-other-important-information">See more</a></li>
</ul>
</div>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>Current Stable Tag </strong></p>



<p>
	<img alt="👉" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f449.png" style="height: 1em;" /> <a href="https://downloads.wordpress.org/plugin/woocommerce.10.6.2.zip"><strong>WooCommerce 10.6.2</strong></a>
</p>



<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<p class="has-small-font-size"><strong>About: </strong></p>



<ul class="wp-block-list has-small-font-size" style="margin-top: 0; margin-bottom: 0;">
<li><img alt="✅" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/2705.png" style="height: 1em;" /> Backwards compatible</li>



<li>Commits: <strong>299</strong></li>



<li>Contributors: <strong>80</strong></li>
</ul>
</div>
</div>
</div>
</div>



<h2 class="wp-block-heading">What&#8217;s Coming in 10.6</h2>



<ul class="wp-block-list">
<li><a href="#whats-coming-in-10.6">What&#8217;s Coming in 10.6</a></li>



<li><a href="#h-feature-highlight-1">Product Collections get more intuitive</a></li>



<li><a href="#h-feature-highlight-2">Visual refinements on Cart and Checkout Blocks</a></li>



<li><a href="#h-feature-highlight-3">Our commitment to improving performance continues</a></li>



<li><a href="#h-more-new-features-and-updates">More new features and updates</a></li>



<li><a href="#h-api-updates">API Updates</a></li>



<li><a href="#h-other-important-information">Other important information</a></li>



<li><a href="#h-database-updates">Database updates</a></li>



<li><a href="#h-changelog">Changelog</a></li>



<li><a href="#h-get-woocommerce-x-x">Get WooCommerce 10.6</a></li>



<li><a href="#h-code-contributors">Code Contributors</a></li>
</ul>



<span id="more-8769843"></span>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-1">Product Collections get more intuitive</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Product Collection: Handpicked Products should start with product picker&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/62989">#62989</a></li>



<li>Products by Brand: journey starts with brand picker&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/63023">#63023</a></li>



<li>Products by Tag/Category: journey starts with taxonomy picker <a href="https://github.com/woocommerce/woocommerce/pull/62993">#62993</a></li>
</ul>



<div class="wp-block-group has-base-background-color has-background is-layout-flow wp-block-group-is-layout-flow">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-full has-custom-border"><img alt="User interface displaying options to select types of products to showcase, including Featured Products, New Arrivals, On Sale Products, and more." class="wp-image-8769847" height="878" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/03/Screenshot-2026-03-06-at-11.20.01-AM.png" style="border-radius: 6px;" width="1474" /></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-full has-custom-border"><img alt="User interface for product selection in a clothing collection, showing options like cashmere and wool sweaters." class="wp-image-8769848" height="1404" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/03/Screenshot-2026-03-06-at-11.20.46-AM.png" style="border-top-left-radius: 6px; border-top-right-radius: 6px; border-bottom-left-radius: 6px; border-bottom-right-radius: 6px;" width="1450" /></figure>
</div>
</div>
</div>



<p>New updates to Product Collections include more collection options (including Products by Brand) and a better interface for selecting products, categories, or other configurations when adding a new collection to a page. </p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-2">Visual refinements on Cart and Checkout Blocks</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Position the remove button to the right of the quantity picker and use trash icon instead of text&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/62965">#62965</a></li>



<li>Move product sale badge alongside individual prices in cart and update design&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/63012">#63012</a></li>
</ul>



<div class="wp-block-group has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-c385debf wp-block-group-is-layout-constrained">
<figure class="wp-block-image size-full has-custom-border"><img alt="A product list featuring three clothing items: a green cashmere crewneck sweater, a black cashmere blend scarf, and a gray wool turtleneck sweater, along with their prices and sizes." class="wp-image-8769851" height="1052" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/03/Screenshot-2026-03-09-at-10.37.05-AM.png" style="border-radius: 6px;" width="1834" /></figure>
</div>



<p>The Cart and Checkout Blocks continue to get design polish and improvements, including a new trash icon for removing items from the cart, cleaner font sizes and spacing for more compact product meta information, and an updated price savings badge. </p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-3">Our commitment to improving performance continues</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Recent Reviews widget: address slow SQL query (take 2) <a href="https://github.com/woocommerce/woocommerce/pull/63224">#63224</a></li>



<li>Products: reduce the number of SQLs when rendering related/upsell products.&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/63006">#63006</a></li>



<li>Admin: optimize SQL fetching dates for month filter on orders page&nbsp;<a href="https://github.com/woocommerce/woocommerce/pull/63039">#63039</a><br />and <a href="https://github.com/woocommerce/woocommerce/pulls?q=is%3Apr+%5Bperformance%5D+milestone%3A10.6.0">many others</a></li>
</ul>



<p>Database efficiency improves across the board in WooCommerce 10.6. Checkout and admin pages execute fewer SQL queries through smarter caching and deferred cleanup tasks. The Recent Reviews widget now loads asynchronously to prevent admin lockouts, while product pages benefit from consolidated cache management that reduces redundant queries for related and upsell products.</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-more-new-features-and-updates">More new features and updates</h2>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<div class="wp-block-group has-global-padding is-layout-constrained wp-container-core-group-is-layout-7ea68cf2 wp-block-group-is-layout-constrained" style="border-right-width: 1px;">
<p><strong>Menu Order Sorting for Product Filters</strong></p>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Taxonomy Filters: add option to order terms by <code>menu_order</code> <a href="https://github.com/woocommerce/woocommerce/pull/62940">#62940</a></li>
</ul>



<p>Product Filters blocks now respect custom taxonomy ordering, allowing merchants to display categories and brands in the exact order they&#8217;ve set via drag-and-drop in the WordPress admin.</p>



<details class="wp-block-details is-layout-flow wp-block-details-is-layout-flow">See more info
<div class="wp-block-group has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-c385debf wp-block-group-is-layout-constrained">
<figure class="wp-block-image size-full has-custom-border"><img alt="" class="wp-image-8769853" height="988" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/03/Screenshot-2026-03-09-at-11.42.21-AM.png" style="border-top-left-radius: 6px; border-top-right-radius: 6px; border-bottom-left-radius: 6px; border-bottom-right-radius: 6px;" width="934" /></figure>
</div>
</details>
</div>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<div class="wp-block-group has-global-padding is-layout-constrained wp-container-core-group-is-layout-7ea68cf2 wp-block-group-is-layout-constrained" style="border-right-width: 1px;">
<p><strong>Tax calculations can now include shipping costs for stores needing compliance</strong></p>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Add filter for tax-inclusive shipping prices <a href="https://github.com/woocommerce/woocommerce/pull/62944">#62944</a></li>
</ul>



<p>A new filter enables tax-inclusive shipping pricing for EU compliance, allowing merchants to display fixed shipping costs that remain constant regardless of VAT rate—essential for meeting consumer protection laws in Germany, Switzerland, and other EU countries.</p>



<details class="wp-block-details is-layout-flow wp-block-details-is-layout-flow">See more info
<p>Use the filter to always return <code>true</code>, or else add custom logic based on the customer&#8217;s location:</p>



<div class="wp-block-a8c-docs-syntax-highlighting a8c-docs-syntax"><pre class="line-numbers prism-large"><code class="lang-php">add_filter( 'woocommerce_shipping_prices_include_tax', '__return_true' );</code></pre><textarea class="a8c-docs-syntax__copy-textarea">add_filter( 'woocommerce_shipping_prices_include_tax', '__return_true' );</textarea><button class="a8c-docs-syntax__copy-button" type="button"><span class="a8c-docs-syntax__copy-button__before">Copy</span><span class="a8c-docs-syntax__copy-button__after">Copied</span></button></div>
</details>
</div>
</div>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-api-updates">API Updates</h2>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<p><strong>Experimental REST API caching improvements</strong><br />Caching capabilities are being extended to more endpoints. This release adds caching for taxes, currencies, countries, and continents endpoints along with additional validation. </p>



<p>Learn more about this beta feature by reading&nbsp;<a href="https://developer.woocommerce.com/2026/01/23/call-for-testing-experimental-rest-api-caching-in-woocommerce-10-5/">Call for testing: Experimental REST API Caching in WooCommerce 10.5</a></p>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-other-important-information">Other important information</h2>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<p><strong>WooCommerce 10.6 included a number of important developer advisories:</strong></p>



<p id="h-important-update-1"><a href="https://developer.woocommerce.com/2026/02/20/product-images-are-now-lazy-loaded-by-default-in-woocommerce-10-6/"><strong>Product images are now lazy-loaded by default in WooCommerce 10.6</strong></a>&nbsp;– WooCommerce 10.6 introduces lazy loading for Product Image block by default. Developers can customize this behavior using the new&nbsp;<code>woocommerce_product_image_loading_attr</code>&nbsp;filter.</p>



<p><a href="https://developer.woocommerce.com/2026/02/23/second-parameter-of-woocommerce_get_breadcrumb-may-be-null-for-core-breadcrumbs-block-in-woocommerce-10-6/"><strong>Second parameter of woocommerce_get_breadcrumb may be null for Core Breadcrumbs block in WooCommerce 10.6</strong></a>&nbsp;– WooCommerce 10.6 introduces an integration with the WordPress Core Breadcrumbs block, but developers using this filter may need to add a null check.</p>



<p><a href="https://developer.woocommerce.com/2026/02/23/restricting-per_page-for-product-and-productreview-store-api-requests-in-woocommerce-10-6/"><strong>Restricting per_page for Product and ProductReview Store API Requests in WooCommerce 10.6</strong></a>&nbsp;– WooCommerce 10.6 introduces a minimum per_page value of 1 for products StoreAPI endpoints. Developers using per_page=0 will need to implement pagination instead.</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<p><strong>For more, read our post breaking down <a href="https://developer.woocommerce.com/2026/02/23/woocommerce-10-6-whats-coming-for-developers/" id="8769783" type="post">important changes for developers in WooCommerce 10.6</a>.</strong></p>
</div>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<h3 class="wp-block-heading" id="h-database-updates">Database updates</h3>



<p class="has-small-font-size"><img alt="📀" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f4c0.png" style="height: 1em;" /> <code>wc_update_1060_add_woo_idx_comment_approved_type_index</code> (<a href="https://github.com/woocommerce/woocommerce/pull/62805" rel="noreferrer noopener" target="_blank">#62805</a>)</p>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-changelog">Changelog</h2>



<div class="wp-block-group alignwide has-global-padding is-layout-constrained wp-container-core-group-is-layout-c697f43c wp-block-group-is-layout-constrained">
<p>View the full <a href="https://github.com/woocommerce/woocommerce/blob/10.6.0/plugins/woocommerce/readme.txt">changelog</a>.</p>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<h2 class="wp-block-heading" id="h-get-woocommerce-x-x">Get WooCommerce 10.6</h2>



<p class="has-small-font-size"><img alt="👉" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f449.png" style="height: 1em;" /> <strong>To upgrade:</strong> See our <a href="https://docs.woocommerce.com/document/how-to-update-woocommerce/">update guide</a> or  <a href="https://wordpress.org/plugins/woocommerce/">download the latest release from WordPress.org</a>.</p>



<p><img alt="🐞" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f41e.png" style="height: 1em;" /> <strong>Found a Bug?</strong> Please <a href="https://github.com/woocommerce/woocommerce/issues/new?assignees=&amp;labels=&amp;template=1-bug-report.yml&amp;title=[10.6]:%20Title%20of%20the%20issue">submit a report it on GitHub</a>.</p>
</div>



<h2 class="wp-block-heading" id="h-code-contributors">Code Contributors</h2>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/albarin" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/186112?v=4" /></a><figcaption class="wp-element-caption">albarin</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/aldavigdis" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/191583?v=4" /></a><figcaption class="wp-element-caption">aldavigdis</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/mukeshpanchal27" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/10103365?v=4" /></a><figcaption class="wp-element-caption">mukeshpanchal27</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/kkmuffme" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/11071985?v=4" /></a><figcaption class="wp-element-caption">kkmuffme</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/vbelolapotkov" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3139099?v=4" /></a><figcaption class="wp-element-caption">vbelolapotkov</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/johanmolen" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/8382746?v=4" /></a><figcaption class="wp-element-caption">johanmolen</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/matt-h" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/664294?v=4" /></a><figcaption class="wp-element-caption">matt-h</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/AbdullahAymanMSRE" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/63800091?v=4" /></a><figcaption class="wp-element-caption">AbdullahAymanMSRE</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Ninos" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1012403?v=4" /></a><figcaption class="wp-element-caption">Ninos</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/faisuc" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/7190009?v=4" /></a><figcaption class="wp-element-caption">faisuc</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/rsov" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/5605692?v=4" /></a><figcaption class="wp-element-caption">rsov</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/devanshijoshi9" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/86941664?v=4" /></a><figcaption class="wp-element-caption">devanshijoshi9</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/masteradhoc" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/6242098?v=4" /></a><figcaption class="wp-element-caption">masteradhoc</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/dev-shahed" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/125728402?v=4" /></a><figcaption class="wp-element-caption">dev-shahed</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/ObliviousHarmony" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/6451942?v=4" /></a><figcaption class="wp-element-caption">ObliviousHarmony</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/triple0t" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/30554163?v=4" /></a><figcaption class="wp-element-caption">triple0t</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/alexandre-khoury" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/102443514?v=4" /></a><figcaption class="wp-element-caption">alexandre-khoury</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/superdav42" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1534605?v=4" /></a><figcaption class="wp-element-caption">superdav42</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/opr" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/5656702?v=4" /></a><figcaption class="wp-element-caption">opr</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/deepaklalwani97" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/32839217?v=4" /></a><figcaption class="wp-element-caption">deepaklalwani97</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/lucatume" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/2749650?v=4" /></a><figcaption class="wp-element-caption">lucatume</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/markoskiz" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/118370925?v=4" /></a><figcaption class="wp-element-caption">markoskiz</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/KokkieH" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/11873759?v=4" /></a><figcaption class="wp-element-caption">KokkieH</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/vreoo" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/74427567?v=4" /></a><figcaption class="wp-element-caption">vreoo</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/prettyboymp" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/103718?v=4" /></a><figcaption class="wp-element-caption">prettyboymp</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/rnayabed" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/25760501?v=4" /></a><figcaption class="wp-element-caption">rnayabed</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/barryhughes" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3594411?v=4" /></a><figcaption class="wp-element-caption">barryhughes</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/lysyjan" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/13644846?v=4" /></a><figcaption class="wp-element-caption">lysyjan</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/youknowriad" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/272444?v=4" /></a><figcaption class="wp-element-caption">youknowriad</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/kmanijak" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/20098064?v=4" /></a><figcaption class="wp-element-caption">kmanijak</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/straku" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/8038404?v=4" /></a><figcaption class="wp-element-caption">straku</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/catthetech" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/88114675?v=4" /></a><figcaption class="wp-element-caption">catthetech</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/bor0" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1620929?v=4" /></a><figcaption class="wp-element-caption">bor0</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/jilani53" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/11515098?v=4" /></a><figcaption class="wp-element-caption">jilani53</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/kalessil" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1577185?v=4" /></a><figcaption class="wp-element-caption">kalessil</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/mcliwanow" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/4765119?v=4" /></a><figcaption class="wp-element-caption">mcliwanow</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/frosso" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/273592?v=4" /></a><figcaption class="wp-element-caption">frosso</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/malinajirka" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/2261188?v=4" /></a><figcaption class="wp-element-caption">malinajirka</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/anomiex" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1030580?v=4" /></a><figcaption class="wp-element-caption">anomiex</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/bacoords" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/6867360?v=4" /></a><figcaption class="wp-element-caption">bacoords</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Mayisha" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/33387139?v=4" /></a><figcaption class="wp-element-caption">Mayisha</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/allilevine" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1689238?v=4" /></a><figcaption class="wp-element-caption">allilevine</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/luisherranz" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3305402?v=4" /></a><figcaption class="wp-element-caption">luisherranz</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/haszzam" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/42672551?v=4" /></a><figcaption class="wp-element-caption">haszzam</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/adimoldovan" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3854374?v=4" /></a><figcaption class="wp-element-caption">adimoldovan</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/oaratovskyi" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/79862886?v=4" /></a><figcaption class="wp-element-caption">oaratovskyi</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/georgestephanis" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/941023?v=4" /></a><figcaption class="wp-element-caption">georgestephanis</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/peterwilsoncc" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/519727?v=4" /></a><figcaption class="wp-element-caption">peterwilsoncc</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Reethum6" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/169574036?v=4" /></a><figcaption class="wp-element-caption">Reethum6</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/yuliyan" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/2722412?v=4" /></a><figcaption class="wp-element-caption">yuliyan</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/hannahtinkler" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/7140719?v=4" /></a><figcaption class="wp-element-caption">hannahtinkler</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/wjrosa" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/10187816?v=4" /></a><figcaption class="wp-element-caption">wjrosa</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/jonas-hoebenreich" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/64426524?v=4" /></a><figcaption class="wp-element-caption">jonas-hoebenreich</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/nerrad" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1429108?v=4" /></a><figcaption class="wp-element-caption">nerrad</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/anandrajaram21" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/48560219?v=4" /></a><figcaption class="wp-element-caption">anandrajaram21</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/helgatheviking" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/507025?v=4" /></a><figcaption class="wp-element-caption">helgatheviking</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/samueljseay" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1281828?v=4" /></a><figcaption class="wp-element-caption">samueljseay</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Konamiman" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/937723?v=4" /></a><figcaption class="wp-element-caption">Konamiman</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/luizreis" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/7714042?v=4" /></a><figcaption class="wp-element-caption">luizreis</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Copilot" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/in/1143301?v=4" /></a><figcaption class="wp-element-caption">Copilot</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/costasovo" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1082140?v=4" /></a><figcaption class="wp-element-caption">costasovo</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/pavel-mailpoet" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/29194603?v=4" /></a><figcaption class="wp-element-caption">pavel-mailpoet</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/czarflix" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/89711008?v=4" /></a><figcaption class="wp-element-caption">czarflix</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/dmallory42" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/11770181?v=4" /></a><figcaption class="wp-element-caption">dmallory42</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/leonardola" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/6342964?v=4" /></a><figcaption class="wp-element-caption">leonardola</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/ayushpahwa" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/8526215?v=4" /></a><figcaption class="wp-element-caption">ayushpahwa</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/RistoNiinemets" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3982627?v=4" /></a><figcaption class="wp-element-caption">RistoNiinemets</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/arcangelini" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/33258733?v=4" /></a><figcaption class="wp-element-caption">arcangelini</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/serhiilabs" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/47003509?v=4" /></a><figcaption class="wp-element-caption">serhiilabs</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/amitraj2203" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/77401999?v=4" /></a><figcaption class="wp-element-caption">amitraj2203</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/Aljullu" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3616980?v=4" /></a><figcaption class="wp-element-caption">Aljullu</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/bhavz-10" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/53536925?v=4" /></a><figcaption class="wp-element-caption">bhavz-10</figcaption></figure>
</div>
</div>



<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/jorgeatorres" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/184724?v=4" /></a><figcaption class="wp-element-caption">jorgeatorres</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/SantosGuillamot" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/34552881?v=4" /></a><figcaption class="wp-element-caption">SantosGuillamot</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/chihsuan" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/4344253?v=4" /></a><figcaption class="wp-element-caption">chihsuan</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/daledupreez" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/3376401?v=4" /></a><figcaption class="wp-element-caption">daledupreez</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/ebinnion" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/1126811?v=4" /></a><figcaption class="wp-element-caption">ebinnion</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><a href="https://github.com/kraftbj" target="_blank"><img alt="" src="https://avatars.githubusercontent.com/u/88897?v=4" /></a><figcaption class="wp-element-caption">kraftbj</figcaption></figure>
</div>
</div>
<p>The post <a href="https://developer.woocommerce.com/2026/03/10/woocommerce-10-6-enhanced-blocks-and-a-faster-dashboard/">WooCommerce 10.6: Enhanced blocks and a faster dashboard</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
