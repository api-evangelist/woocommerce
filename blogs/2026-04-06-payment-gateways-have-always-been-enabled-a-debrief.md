---
title: "Payment gateways have always been enabled: A debrief"
url: "https://developer.woocommerce.com/2026/04/06/payment-gateways-have-always-been-enabled-a-debrief/"
date: "Mon, 06 Apr 2026 15:26:48 +0000"
author: "Shani Banerjee"
feed_url: "https://developer.woocommerce.com/feed/"
---
<p><strong>If you updated WooCommerce PayPal Payments recently and woke up to a flood of &#8220;payment gateway enabled&#8221; emails, here&#8217;s what happened and what it means for your store.</strong></p>



<h2 class="wp-block-heading">Payment gateways were always enabled</h2>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>TL;DR:</strong> Updating WooCommerce PayPal Payments to v4.0.0 converts previously hidden Alternative Payment Methods (APMs) into individual WooCommerce gateways, triggering &#8220;payment gateway enabled&#8221; notifications for methods that were already active. Nothing new was turned on. You can review and manage these methods individually under <strong>WooCommerce &gt; Settings &gt; Payments</strong>.</p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity" />



<p>A thread appeared on the WordPress.org support forums this week from a merchant who received 10 separate notifications informing them that payment gateways had been enabled on their site, methods they had never intentionally configured: Blik, iDEAL, Bancontact, Trustly, Przelewy24, EPS, Multibanco, MyBank, and Standard Card Button.</p>



<p>If you&#8217;ve seen the same thing, <strong>nothing was hacked</strong>. But the experience is a useful reminder of why plugin migration design matters, and why opt-in defaults tend to be the safer path.</p>



<h3 class="wp-block-heading">What actually changed</h3>



<p>In v2 and v3, APMs were available by default as part of the PayPal smart button stack. They weren&#8217;t exposed as standalone WooCommerce payment gateways and visible as additional buttons within the PayPal button UI, with visibility determined by the buyer&#8217;s IP address (Dutch IP = iDEAL, Belgian IP = Bancontact, and so on). Most merchants had no idea these were running, because there was no separate WooCommerce settings entry for them. The only way to disable them was to explicitly add them to a &#8220;disabled APM&#8221; list, something most merchants never did because most merchants didn&#8217;t know it existed.</p>



<p>In v4.0.0, each APM is now its own <strong>individual WooCommerce payment gateway</strong>, with its own settings entry and enable/disable toggle and visibility determined by the buyer&#8217;s billing country. This is a more transparent and manageable model. The problem is that the migration preserved the existing configuration rather than defaulting everything to disabled, which was the right call for continuity, but meant WooCommerce&#8217;s built-in notification system treated a structural migration as a batch of new gateway activations.</p>



<p><strong>Nothing new was turned on. What changed was the architecture, and the notification system fired accordingly.</strong></p>



<h3 class="wp-block-heading">What to do now</h3>



<p>Your checkout behavior hasn&#8217;t changed. Buyers in eligible countries were already seeing these payment methods before you updated. You can now manage each APM individually from <strong>WooCommerce &gt; Settings &gt; Payments</strong> and you can enable or disable them based on what makes sense for your store and customer base. The <a href="https://woocommerce.com/document/woocommerce-paypal-payments/local-payment-methods/">PayPal local payment methods documentation</a> covers which methods are geo-eligible and what each one requires.</p>



<h3 class="wp-block-heading">Takeaways</h3>



<p>The plugin team faced a genuine tradeoff: default everything to disabled and risk breaking checkout for buyers actively using those methods, or preserve the existing state and accept the notification noise. While it was the right call for continuity, what would have helped is a pre-update communication, a clear heads-up explaining what was changing, what state merchants were in, and what action (if any) was needed before upgrading. We try to consider this kind of communication as often as we can, particularly when shipping changes in WooCommerce Core with <a href="https://developer.woocommerce.com">developer advisories</a> ahead of major releases. That said, this was missed, and now we know.</p>



<p>If you have questions, the <a href="https://wordpress.org/support/topic/payment-gateways-enabled-without-consent/">original support thread</a> is a good starting point; the PayPal Payments team is very responsive there. And of course, you can always reach out in the <a href="https://woocommerce.com/community-slack/" id="https://woocommerce.com/community-slack/" type="link">WooCommerce Community Slack</a>, as well as X and Bksky, <code>@DevelopWoo</code>. </p>
<p>The post <a href="https://developer.woocommerce.com/2026/04/06/payment-gateways-have-always-been-enabled-a-debrief/">Payment gateways have always been enabled: A debrief</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
