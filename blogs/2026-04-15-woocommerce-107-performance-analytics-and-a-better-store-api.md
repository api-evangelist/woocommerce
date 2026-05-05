---
title: "WooCommerce 10.7: Performance, Analytics, and a better Store API"
url: "https://developer.woocommerce.com/2026/04/15/woocommerce-10-7/"
date: "Wed, 15 Apr 2026 14:50:29 +0000"
author: "Shani Banerjee"
feed_url: "https://developer.woocommerce.com/feed/"
---
<div class="wp-block-group alignwide has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-ea8e1d93 wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>WooCommerce 10.7.0</strong> Has been released on <strong>April, 14, 2026.</strong> This post highlights what&#8217;s new in this version of WooCommerce.</p>



<p class="has-small-font-size">See our <a href="https://docs.woocommerce.com/document/how-to-update-woocommerce/">update guide</a>.<br /><a href="https://wordpress.org/plugins/woocommerce/">Download directly</a> from WordPress.org.</p>



<div class="wp-block-group has-small-font-size has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<p><strong><strong>Other important information:</strong></strong></p>



<ul class="wp-block-list" style="margin-top: 0; margin-bottom: 0;">
<li>This release includes security updates</li>



<li><img alt="📀" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f4c0.png" style="height: 1em;" /> This release <strong>does </strong>include a <a href="#h-database-updates">database update</a>.</li>



<li><a href="#h-other-important-information">See more</a></li>
</ul>
</div>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<p><strong>Current Stable Tag</strong>:</p>



<p><a href="https://downloads.wordpress.org/plugin/woocommerce.10.7.0.zip"><strong>WooCommerce 10.7.0</strong></a></p>



<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
<p class="has-small-font-size"><strong>About: </strong></p>



<ul class="wp-block-list has-small-font-size" style="margin-top: 0; margin-bottom: 0;">
<li><img alt="✅" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/2705.png" style="height: 1em;" /> Backwards compatible</li>



<li>PRs: <strong>175</strong></li>



<li>Contributors: <strong>66</strong></li>
</ul>
</div>
</div>
</div>
</div>



<span id="more-8769940"></span>



<div class="wp-block-yoast-seo-table-of-contents yoast-table-of-contents"><h2>What&#8217;s coming in 10.7</h2><ul><li><a href="#h-feature-highlight-1">Performance enhancements and cache priming brings results</a></li><li><a href="#h-feature-highlight-2">Experimental block-based email editor improvements</a></li><li><a href="#h-feature-highlight-3">Analytics export filters</a></li><li><a href="#h-feature-highlight-4">Accessibility improvements</a></li><li><a href="#h-feature-highlight-5">Cart and Checkout block fixes</a></li><li><a href="#h-more-new-features-and-updates">Order fulfillments gets a proper API (Beta)</a></li><li><a href="#h-api-updates">API Updates</a></li><li><a href="#h-other-important-information">Other important information</a></li><li><a href="#h-changelog">Changelog</a></li><li><a href="#h-get-woocommerce-x-x">Get WooCommerce 10.7</a></li><li><a href="#h-code-contributors">Code Contributors</a></li></ul></div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-1">Performance enhancements and cache priming brings results</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li><strong>HPOS orders: </strong>Cache priming eliminates N+1 queries on <code>/wc/v4/orders</code>  <a href="https://github.com/woocommerce/woocommerce/pull/63440">#63440</a></li>



<li><strong>Checkout: </strong>Reduces the number of SQL queries required to persist a draft order during checkout <a href="https://github.com/woocommerce/woocommerce/pull/63258">#63258</a></li>



<li><strong>Shipping:</strong> New indexes added on <code>woocommerce_shipping_zone_methods</code> (<code>zone_id</code>, <code>method_id</code>) <a href="https://github.com/woocommerce/woocommerce/pull/63674">#63674</a></li>



<li><strong>Store API:</strong> <code>Last-Modified</code> timestamp gets cached on products endpoint, skipping DB query on cache hit <a href="https://github.com/woocommerce/woocommerce/pull/63228">#63228</a></li>



<li><a href="https://github.com/woocommerce/woocommerce/pulls?q=is%3Apr+%5Bperformance%5D+milestone%3A10.7.0">More performance enhancements</a></li>
</ul>



<p>This release delivers some of the most significant query reduction work in recent &#8220;memory.&#8221; The biggest win is on HPOS orders: the <code>/wc/v4/orders</code> endpoint previously triggered 271 database queries per request due to N+1 patterns during REST API serialization. Cache priming now reduces this to 132 queries, a 51% reduction, by preloading order data in bulk before serialization begins.</p>



<p>As a comparison, Checkout performance without object cache enabled can drop SQL queries from the 204 to 172 range. However, with object cache enabled, the reduction is more noticeable, ranging from 127 queries to as low as 115. </p>



<p>Additionally, a new <code>woocommerce_pre_refresh_order_count_cache</code> filter lets extensions and plugins skip redundant order count refreshes in high-traffic scenarios where the count cache is already being managed externally:</p>



<pre class="wp-block-code"><code>add_filter( 'woocommerce_pre_refresh_order_count_cache', '__return_true' );</code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-2">Experimental block-based email editor improvements</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Add &#8211; <code>alignfull</code> block support via root padding distribution in <code>Content_Renderer</code> <a href="https://github.com/woocommerce/woocommerce/pull/63752">#63752</a></li>



<li>Add &#8211; Rich WordPress embed cards: featured image, title, excerpt (5-card cap, 1-day transient TTL) <a href="https://github.com/woocommerce/woocommerce/pull/63542">#63542</a></li>



<li>Fix &#8211; Redundant CSS inlining consolidated to a single pass <a href="https://github.com/woocommerce/woocommerce/pull/63454">#63454</a></li>



<li>Add &#8211;  New <code>woocommerce_email_block_template_html</code> filter for customizing reset template content <a href="https://github.com/woocommerce/woocommerce/pull/63558">#63558</a></li>



<li>Add &#8211;  New <code>woocommerce_email_editor_send_button_disabled</code> filter for auto-save before send workflows <a href="https://github.com/woocommerce/woocommerce/pull/63722">#63722</a></li>
</ul>



<div class="wp-block-group has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-c385debf wp-block-group-is-layout-constrained">
<figure class="wp-block-image size-large"><img alt="After: WordPress embed block in email rendered as a rich card with featured image, title, and excerpt" src="https://github.com/user-attachments/assets/9fd90481-01a3-4f0e-bd06-b6293b36e2ed" /><figcaption class="wp-element-caption">After: rich embed card</figcaption></figure>
</div>



<p>The email editor remains behind a feature flag in Woo core. WordPress embed blocks now render as rich cards with a featured image, post title, excerpt, and site icon; they were previously rendered as plain links. Cards are cached via transient with a 1-day TTL and capped at 5 per email for performance.</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-3">Analytics export filters</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Fix &#8211; Adds export column/item filters and forward currency from URL query <a href="https://github.com/woocommerce/woocommerce/pull/63618">#63618</a></li>
</ul>



<pre class="wp-block-code"><code>add_filter( 'woocommerce_report_revenue_stats_export_columns', function( $columns ) {
    $columns['my_custom_column'] = __( 'My Column', 'my-plugin' );
    return $columns;
} );
add_filter( 'woocommerce_report_revenue_stats_prepare_export_item', function( $item, $row ) {
    $item['my_custom_column'] = $row['my_data'] ?? '';
    return $item;
}, 10, 2 );</code></pre>



<p>Analytics exports now correctly forward currency context and any custom filter parameters to background jobs. Previously, background export jobs ran without these parameters, causing exported data to not match what was visible in the UI for multicurrency setups. The new filters let you customize export columns and row data per report type.</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-4">Accessibility improvements</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Fix &#8211; System Status page: green status indicators now meet WCAG 2.2 AA contrast requirements <a href="https://github.com/woocommerce/woocommerce/pull/63746">#63746</a></li>



<li>Fix &#8211; Dashboard widget and checkout element contrast fixes <a href="https://github.com/woocommerce/woocommerce/pull/63522">#63522</a> <a href="https://github.com/woocommerce/woocommerce/pull/63521">#63521</a></li>
</ul>



<div class="wp-block-group has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-c385debf wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><img alt="" class="wp-image-8769941" height="713" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/04/image.png?w=1024" width="1024" /><figcaption class="wp-element-caption">Before</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><img alt="" class="wp-image-8769942" height="713" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/04/image_310871.png?w=1024" width="1024" /><figcaption class="wp-element-caption">After</figcaption></figure>
</div>
</div>
</div>



<p>Shortcode checkout validated field border now uses the updated <code>--wc-green</code> variable and <code>var(--wc-subtext</code> .</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-feature-highlight-5">Cart and Checkout block fixes</h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Fix &#8211; Nonce fetched fresh on cart store init, awaited before POST operations <a href="https://github.com/woocommerce/woocommerce/pull/62892">#62892</a></li>



<li>Update &#8211; Payment method radio always shown with a single option <a href="https://github.com/woocommerce/woocommerce/pull/63351">#63351</a></li>



<li>Color inheritance fixes for dark mode form elements.</li>
</ul>



<div class="wp-block-group has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-c385debf wp-block-group-is-layout-constrained">
<div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><img alt="" class="wp-image-8769943" height="352" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/04/image_ad3d58.png?w=1024" width="1024" /><figcaption class="wp-element-caption">Before</figcaption></figure>
</div>



<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
<figure class="wp-block-image size-large"><img alt="" class="wp-image-8769944" height="853" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/04/image_86886f.png?w=1024" width="1024" /><figcaption class="wp-element-caption">After</figcaption></figure>
</div>
</div>
</div>



<p>The payment method radio button is now always rendered, even when only a single payment method is available. Previously, the radio was hidden for single-option checkouts, which caused the payment method label and description to visually merge in a confusing way.</p>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-more-new-features-and-updates">Order fulfillments gets a proper API <em>(Beta)</em></h2>



<ul class="wp-block-list is-style-checkmark-list has-small-font-size">
<li>Typed PHP methods: <code>get_tracking_number()</code>, <code>set_tracking_number()</code>, <code>get_shipping_provider()</code>, <code>set_shipping_provider()</code> <a href="https://github.com/woocommerce/woocommerce/pull/63573">#63573</a></li>



<li>New <code>FULFILLMENT</code> order note group constant in <code>OrderNoteGroup</code> <a href="https://github.com/woocommerce/woocommerce/pull/63516">#63516</a></li>



<li>Data store registered via <code>woocommerce_data_stores</code> filter, enabling extension override <a href="https://github.com/woocommerce/woocommerce/pull/63485">#63485</a></li>



<li>Namespace moved: <code>Automattic\WooCommerce\Internal\Fulfillments</code> → <code>Automattic\WooCommerce\Admin\Features\Fulfillments</code></li>
</ul>



<p>While Fulfillments remains a beta feature, it receives a significant update in 10.7. Custom shipping providers are now accessible through settings: merchants define them via <code>Settings &gt; Shipping &gt; Shipping Providers</code>, backed by the new <code>wc_fulfillment_shipping_provider</code> taxonomy. Each provider supports a tracking URL template, and the orders list gains a filter dropdown for the new providers.</p>



<p>The PHP API is now fully typed so you can interact with fulfillment tracking data like this:</p>



<pre class="wp-block-code"><code>$fulfillment->get_tracking_number();
$fulfillment->set_tracking_number( '1Z999AA10123456784' );
$fulfillment->get_shipping_provider();
$fulfillment->set_shipping_provider( 'ups' );</code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-api-updates">API Updates</h2>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<ul class="wp-block-list">
<li>Customer <code>username</code> and <code>password</code> fields now always optional, auto-generated when empty <a href="https://github.com/woocommerce/woocommerce/pull/63536">#63536</a></li>



<li>Refund amount comparison now uses proper precision rounding, preventing false &#8220;amount cannot be less than line items&#8221; errors <a href="https://github.com/woocommerce/woocommerce/pull/63667">#63667</a></li>
</ul>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-other-important-information">Other important information</h2>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<h3 class="wp-block-heading" id="h-important-update-1"><strong>Security hardening across several surfaces</strong></h3>



<p>XSS protection via <code>wp_kses_post()</code> has been extended to the v4 REST API order notes endpoint (<code>OrderNotes\Controller::create_item()</code>), matching the protection already in place for v1 through v3 <a href="https://github.com/woocommerce/woocommerce/pull/63661">#63661</a>. </p>



<p>CSRF validation via <code>check_ajax_referer()</code> has been added to <code>product_ordering()</code> and <code>term_ordering()</code> AJAX handlers <a href="https://github.com/woocommerce/woocommerce/pull/63422">#63422</a>. </p>



<p>Payment gateway password fields now use <code>trim()</code> instead of <code>sanitize_text_field()</code>, preserving <code>%</code> characters that were previously being stripped <a href="https://github.com/woocommerce/woocommerce/pull/63597">#63597</a>.</p>
</div>



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<h3 class="wp-block-heading" id="h-database-updates">Database updates</h3>



<p class="has-small-font-size"><img alt="📀" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f4c0.png" style="height: 1em;" /> Deprecate &#8211; <strong><code>wc_update_1070_disable_hpos_sync_on_read</code></strong>  <a href="https://github.com/woocommerce/woocommerce/pull/63175">#63175</a></p>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<h2 class="wp-block-heading" id="h-changelog">Changelog</h2>



<div class="wp-block-group alignwide has-global-padding is-layout-constrained wp-container-core-group-is-layout-c697f43c wp-block-group-is-layout-constrained">
<p>View the full <a href="https://github.com/woocommerce/woocommerce/blob/10.7.0/plugins/woocommerce/readme.txt">changelog</a>. </p>
</div>



<hr class="wp-block-separator has-alpha-channel-opacity is-style-wide" />



<div class="wp-block-group alignwide has-border-color has-base-background-color has-background has-global-padding is-layout-constrained wp-container-core-group-is-layout-d6eb7fa6 wp-block-group-is-layout-constrained">
<h2 class="wp-block-heading" id="h-get-woocommerce-x-x">Get WooCommerce 10.7</h2>



<p class="has-small-font-size"><img alt="👉" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f449.png" style="height: 1em;" /> <strong>To upgrade:</strong> See our <a href="https://docs.woocommerce.com/document/how-to-update-woocommerce/">update guide</a> or  <a href="https://wordpress.org/plugins/woocommerce/">download the latest release from WordPress.org</a>.</p>



<p><img alt="🐞" class="wp-smiley" src="https://s.w.org/images/core/emoji/17.0.2/72x72/1f41e.png" style="height: 1em;" /> <strong>Found a Bug?</strong> Please <a href="https://github.com/woocommerce/woocommerce/issues/new?assignees=&amp;labels=&amp;template=1-bug-report.yml&amp;title=[10.7%20release]:%20Title%20of%20the%20issue">submit a report on GitHub</a>.</p>
</div>



<h2 class="wp-block-heading" id="h-code-contributors">Code Contributors</h2>




        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/vladolaru" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/8830539?v=4" />
    </a>
    <figcaption>vladolaru</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/Abdalsalaam" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/19236737?v=4" />
    </a>
    <figcaption>Abdalsalaam</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/szepeviktor" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/952007?v=4" />
    </a>
    <figcaption>szepeviktor</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/triple0t" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/30554163?v=4" />
    </a>
    <figcaption>triple0t</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/ObliviousHarmony" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/6451942?v=4" />
    </a>
    <figcaption>ObliviousHarmony</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/jorgeatorres" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/184724?v=4" />
    </a>
    <figcaption>jorgeatorres</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/shameemreza" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/14240438?v=4" />
    </a>
    <figcaption>shameemreza</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/SantosGuillamot" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/34552881?v=4" />
    </a>
    <figcaption>SantosGuillamot</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/lucatume" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/2749650?v=4" />
    </a>
    <figcaption>lucatume</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/staskus" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/4062343?v=4" />
    </a>
    <figcaption>staskus</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/albarin" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/186112?v=4" />
    </a>
    <figcaption>albarin</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/mordeth" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/8667118?v=4" />
    </a>
    <figcaption>mordeth</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/samnajian" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/789421?v=4" />
    </a>
    <figcaption>samnajian</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/kalessil" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1577185?v=4" />
    </a>
    <figcaption>kalessil</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/Anuj-Rathore24" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/80690679?v=4" />
    </a>
    <figcaption>Anuj-Rathore24</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/lysyjan" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/13644846?v=4" />
    </a>
    <figcaption>lysyjan</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/hannahtinkler" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/7140719?v=4" />
    </a>
    <figcaption>hannahtinkler</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/Aljullu" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/3616980?v=4" />
    </a>
    <figcaption>Aljullu</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/nerrad" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1429108?v=4" />
    </a>
    <figcaption>nerrad</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/gutobenn" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/607762?v=4" />
    </a>
    <figcaption>gutobenn</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/mikejolley" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/90977?v=4" />
    </a>
    <figcaption>mikejolley</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/prettyboymp" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/103718?v=4" />
    </a>
    <figcaption>prettyboymp</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/luisherranz" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/3305402?v=4" />
    </a>
    <figcaption>luisherranz</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/opr" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/5656702?v=4" />
    </a>
    <figcaption>opr</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/JimmyAppelt" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/5420393?v=4" />
    </a>
    <figcaption>JimmyAppelt</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/straku" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/8038404?v=4" />
    </a>
    <figcaption>straku</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/leonardola" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/6342964?v=4" />
    </a>
    <figcaption>leonardola</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/pavel-mailpoet" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/29194603?v=4" />
    </a>
    <figcaption>pavel-mailpoet</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/Mayisha" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/33387139?v=4" />
    </a>
    <figcaption>Mayisha</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/tpaksu" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/3295?v=4" />
    </a>
    <figcaption>tpaksu</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/raicem" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/10389957?v=4" />
    </a>
    <figcaption>raicem</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/samueljseay" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1281828?v=4" />
    </a>
    <figcaption>samueljseay</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/faisuc" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/7190009?v=4" />
    </a>
    <figcaption>faisuc</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/bhavz-10" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/53536925?v=4" />
    </a>
    <figcaption>bhavz-10</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/wjrosa" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/10187816?v=4" />
    </a>
    <figcaption>wjrosa</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/BurakParsAydin" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/6393475?v=4" />
    </a>
    <figcaption>BurakParsAydin</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/kraftbj" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/88897?v=4" />
    </a>
    <figcaption>kraftbj</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/sunyatasattva" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1847066?v=4" />
    </a>
    <figcaption>sunyatasattva</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/Dekadinious" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/37292177?v=4" />
    </a>
    <figcaption>Dekadinious</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/mukeshpanchal27" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/10103365?v=4" />
    </a>
    <figcaption>mukeshpanchal27</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/jimjasson" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/25955483?v=4" />
    </a>
    <figcaption>jimjasson</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/oaratovskyi" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/79862886?v=4" />
    </a>
    <figcaption>oaratovskyi</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/kmanijak" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/20098064?v=4" />
    </a>
    <figcaption>kmanijak</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/costasovo" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1082140?v=4" />
    </a>
    <figcaption>costasovo</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/yuliyan" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/2722412?v=4" />
    </a>
    <figcaption>yuliyan</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/jacobmax" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/2515292?v=4" />
    </a>
    <figcaption>jacobmax</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/alopezari" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/45979455?v=4" />
    </a>
    <figcaption>alopezari</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/AhmarZaidi" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/71930390?v=4" />
    </a>
    <figcaption>AhmarZaidi</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/tiago-123" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/77335756?v=4" />
    </a>
    <figcaption>tiago-123</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/darcie" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/318285?v=4" />
    </a>
    <figcaption>darcie</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/deepaklalwani97" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/32839217?v=4" />
    </a>
    <figcaption>deepaklalwani97</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/chihsuan" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/4344253?v=4" />
    </a>
    <figcaption>chihsuan</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/arcangelini" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/33258733?v=4" />
    </a>
    <figcaption>arcangelini</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/luizreis" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/7714042?v=4" />
    </a>
    <figcaption>luizreis</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/sarahdayan" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/5370675?v=4" />
    </a>
    <figcaption>sarahdayan</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/louwie17" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/2240960?v=4" />
    </a>
    <figcaption>louwie17</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/bor0" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1620929?v=4" />
    </a>
    <figcaption>bor0</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/mcliwanow" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/4765119?v=4" />
    </a>
    <figcaption>mcliwanow</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/helgatheviking" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/507025?v=4" />
    </a>
    <figcaption>helgatheviking</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/adrianlbs" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/6375646?v=4" />
    </a>
    <figcaption>adrianlbs</figcaption>
  </figure>
  
</div>


            
      
      
      
      
        </div>
        
      
    
      
        
        <div class="wp-block-columns is-layout-flex wp-container-core-columns-is-layout-28f84493 wp-block-columns-is-layout-flex">
                
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/jamesckemp" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1853915?v=4" />
    </a>
    <figcaption>jamesckemp</figcaption>
  </figure>
  
</div>

        
            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/allilevine" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1689238?v=4" />
    </a>
    <figcaption>allilevine</figcaption>
  </figure>
  
</div>


            
      
      
      
      
    
      
              
<div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow">
  
  <figure class="wp-block-image size-large">
    <a href="https://github.com/ebinnion" target="_blank">
      <img alt="" src="https://avatars.githubusercontent.com/u/1126811?v=4" />
    </a>
    <figcaption>ebinnion</figcaption>
  </figure>
  
</div>


            
      
      
        
        
          
          <div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow"></div>
          
        
          
          <div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow"></div>
          
        
          
          <div class="wp-block-column is-layout-flow wp-block-column-is-layout-flow"></div>
          
        
      
      
      
        </div>
        
      
<p>The post <a href="https://developer.woocommerce.com/2026/04/15/woocommerce-10-7/">WooCommerce 10.7: Performance, Analytics, and a better Store API</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
