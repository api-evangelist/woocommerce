---
title: "Giving merchants better visibility into the health of their subscriptions"
url: "https://developer.woocommerce.com/2026/04/30/subscriptions-health-check/"
date: "Thu, 30 Apr 2026 21:41:32 +0000"
author: "Darren Ethier"
feed_url: "https://developer.woocommerce.com/feed/"
---
<p>Subscriptions are the lifeblood of successful businesses, building relationships with their customers and establishing a recurring, sustainable income stream. It&#8217;s important that merchants can trust that their subscriptions are working as expected — and when something isn&#8217;t, that they have the tools to see it and act on it.</p>



<p>Today we&#8217;re shipping a new <strong>Subscriptions Health Check</strong> tool in WooCommerce Subscriptions. It gives every merchant running Subscriptions a surface for asking a simple question: <em>which of my subscriptions might not be renewing as expected?</em> The tool is available to every store running Subscriptions, regardless of whether any specific bug affected them.</p>



<p>The rest of this post covers why we&#8217;re shipping this now, how it works, what we investigated along the way, and what we&#8217;re doing differently going forward. If you just want to run the tool, skip to “How to use it”.</p>



<span id="more-8769986"></span>



<h2 class="wp-block-heading" id="h-why-we-broadened-the-tool"><strong>Why we broadened the tool</strong></h2>



<p>While we already had this tool on our roadmap, we accelerated work on it after a public report of four bugs that could have put subscriptions into an unexpected non-renewal state . We investigated each of those and shipped the remaining fix this week (details below). But while we were scoping the detection work, we realised that a subscription stuck in this state is a problem <em>regardless</em> of what caused it.</p>



<p>Bugs are one path to that outcome. A merchant admin toggling a setting is another. A gateway change, a token deletion, an import from another platform, a custom plugin, a third-party integration — all can produce the same observable state: a subscription in the store that <em>could</em> be auto-billing, but isn&#8217;t. Merchants are the only ones with enough store-specific context to tell those cases apart. So instead of building a narrow &#8220;find our bug victims&#8221; detector, we broadened the tool to surface <strong>all</strong> manual-renewal subscriptions that <em>could</em> be running on auto-renewal based on their payment method, as well as subscriptions that might be not have renewed as expected, and let the merchant (or someone acting on their behalf) review them.</p>



<h2 class="wp-block-heading" id="h-how-to-use-it"><strong>How to use it</strong></h2>



<p>The tool lives under <strong>WooCommerce &gt; Status &gt; Subscriptions</strong>. A status card on the Subscriptions Status page also shows when the last scan ran and whether one is currently due.</p>



<figure class="wp-block-image size-large"><img alt="" class="wp-image-8770008" height="508" src="https://developer.woocommerce.com/wp-content/uploads/sites/2/2026/04/image_a7421a.png?w=1024" width="1024" /></figure>



<p>You may trigger a scan immediately with the “Run now” button. Scans process your subscriptions in batches and include throttling to avoid overloading your server or database.</p>



<p>If nightly scans are enabled in <strong>WooCommerce &gt; Settings &gt; Subscriptions</strong>, the tool runs on its own nightly schedule and stores each run&#8217;s results. That means opening the page pulls up the latest scan&#8217;s data — you&#8217;re not waiting on a long query each time. If a scheduled run fails repeatedly, a circuit breaker backs the tool off and tells you on the Status page so you can investigate rather than silently retrying forever.</p>



<p>When you open the tool, you&#8217;ll see three tabs:</p>



<ul class="wp-block-list">
<li><strong>All</strong> — every subscription in the store, for when you want a broader view.</li>



<li><strong>Supports auto-renewal </strong>— subscriptions on your store currently flagged for manual renewal where the customer <em>also</em> has a saved payment token on a gateway that supports automatic billing. These are the ones most likely to warrant review.</li>



<li><strong>Missing renewals</strong> – shows active or on-hold subscriptions that are not set to expire after the current cycle and have an empty next payment date <em>or</em> have a next payment date in the past with no matching renewal order (within a ±24 hour window). The former are subscriptions that are expected to renew but won’t because there’s a missing next payment date, the latter are subscriptions that <em>were</em> expected to renew, but didn’t because no matching renewal order was created. There are different potential causes for either condition to happen including potential plugin/custom code conflicts, server/migration issues, or scheduled actions not running.&nbsp;</li>
</ul>



<h3 class="wp-block-heading" id="h-how-a-subscription-ends-up-on-the-supports-auto-renewal-list"><strong>How a subscription ends up on the &#8220;Supports auto-renewal&#8221; list</strong></h3>



<p>The tool does a single binary decision per subscription. A subscription appears on the list when <em>all</em> of these are true:</p>



<ul class="wp-block-list">
<li>Status is active, on-hold, or pending-cancel</li>



<li>_requires_manual_renewal is true</li>



<li>A payment method is set</li>



<li>That gateway supports subscriptions / automatic recurring payments</li>



<li>The customer has at least one saved payment token on their account for that gateway</li>
</ul>



<p>Everything else (opt-out notes, import-as-manual notes, store-wide &#8220;turn off automatic payments&#8221; settings, prior renewal history) is displayed alongside the subscription rather than used to pre-filter it. That&#8217;s a deliberate choice. Merchants have too much store-specific context for us to guess correctly on their behalf whether a flagged subscription is a real problem or a legitimate manual renewal.</p>



<h3 class="wp-block-heading" id="h-how-a-subscription-ends-up-on-the-missing-renewals-list"><strong>How a subscription ends up on the &#8220;Missing renewals&#8221; list</strong></h3>



<p>Active or on-hold subscriptions appear on the “Missing renewals” list when <em>one</em> of these is true:</p>



<ul class="wp-block-list">
<li>The next payment date is empty, <em>unless</em> the sub is set to expire after the current cycle</li>



<li>The next payment date is in the past with no matching renewal order within a ±24-hour tolerance window</li>
</ul>



<h3 class="wp-block-heading" id="h-what-the-tool-shows-per-row"><strong>What the tool shows per row</strong></h3>



<ul class="wp-block-list">
<li><strong>Subscription</strong> — ID and link to the subscription edit screen.</li>



<li><strong>Created</strong> — creation date.</li>



<li><strong>Customer</strong> — name and link to the user page.</li>



<li><strong>Cycle </strong>— the billing cycle for the subscription.</li>



<li><strong>Status</strong> — the subscription&#8217;s current status.</li>



<li><strong>Billing mode</strong> — manual or automatic.</li>



<li><strong>Renewal preference</strong> — whether the subscriber opted out of auto-renewal via the My Account toggle or whether no preference has been recorded.</li>



<li><strong>Payment method</strong> — the gateway and method currently associated with the subscription.</li>



<li><strong>Next payment date </strong>— the subscription&#8217;s next payment date.</li>



<li><strong>Renewal order status</strong> — status of the most recent renewal order (pending, processing, on-hold, completed, canceled, refunded, or failed).</li>



<li><strong>Last successful payment</strong> — when the subscription last successfully charged, if ever.</li>
</ul>



<p>Subscriptions that were imported as manual from another platform are tagged as such when we can detect the import note, so you can distinguish them at a glance without us hiding them from the list.</p>



<h3 class="wp-block-heading" id="h-filters-you-can-use"><strong>Filters you can use</strong></h3>



<ul class="wp-block-list">
<li><strong>Status</strong> — narrow to a specific subscription status.</li>



<li><strong>Billing mode</strong> — narrow to auto or manual subscriptions.</li>



<li><strong>Renewal order status</strong> — narrow by the status of the last renewal order.</li>



<li><strong>Renewal preference</strong> — show only subscribers who opted out of auto-renewal via the My Account toggle.</li>



<li><strong>Search</strong> — by subscription ID or customer email.</li>
</ul>



<p>Columns are sortable; by default, the list is ordered newest-first.</p>



<h3 class="wp-block-heading" id="h-what-it-deliberately-doesn-t-do"><strong>What it deliberately doesn&#8217;t do</strong></h3>



<ul class="wp-block-list">
<li><strong>It doesn&#8217;t change the subscription without your explicit action.</strong> Only you, the merchant, have the context to decide whether a flagged subscription is a real problem or a legitimate manual renewal on your store.</li>



<li><strong>It doesn&#8217;t pre-filter legitimate manual subscriptions.</strong> The tool doesn&#8217;t automatically exclude subscribers who had opted out of auto-renewal, subscriptions imported as manual from another platform, and stores running with &#8220;Turn off Automatic Payments&#8221; enabled store-wide. Instead, it surfaces all of those but tags them clearly so you can see what&#8217;s going on. Same reasoning: your store, your call.</li>



<li><strong>It doesn&#8217;t try to detect every possible category of subscription problem.</strong> This first version focuses on the auto-renewable-but-flagged-manual and missing renewals population. Other categories are on the list for follow-on iterations.</li>
</ul>



<h2 class="wp-block-heading" id="h-what-we-investigated"><strong>What we investigated</strong></h2>



<p>Some transparency about what we found when we investigated the public report: Four distinct bugs were called out, all four were real, and three were already fixed in previous releases; the fourth shipped this week. But the bugs don&#8217;t all have the same scope or the same impact, and the public discussion has treated them as equivalent in ways that overstate the picture. Any subscription affected by any of these will be surfaced in the Health Check tool if it&#8217;s still in an active billing state, alongside anything else causing the same observable state on your store.</p>



<h3 class="wp-block-heading" id="h-the-four-bugs"><strong>The four bugs</strong></h3>



<p>*Note: &#8220;HPOS&#8221; is an acronym for High Performance Order Storage.</p>



<p><strong>Bug 1 — Stale HPOS cache (fixed in WCS 6.1.0, March 28, 2024).</strong> On HPOS stores, save_dates() didn&#8217;t clear the OrderCache after writing new dates. Any subsequent read of that subscription within the same request or a near-concurrent one, could return a pre-update copy. The fix adds three lines to the HPOS data store: when dates are saved, the cache is invalidated. CPT-only stores were never affected; wp_update_post() and update_post_meta() self-invalidate.</p>



<p><strong>Bug 2 — Missing HPOS backfill methods (fixed in WCS 5.7.0 and 5.8.0, November–December 2023).</strong> On stores running HPOS <em>and</em> data-sync (compatibility) mode, missing get_schedule_* and set_schedule_* methods caused WooCommerce core&#8217;s reflective backfill to skip subscription schedule metadata. Schedule fields — _schedule_next_payment, _schedule_end, and so on — could diverge between wp_wc_orders_meta and wp_postmeta. This is a different failure class from the other three. It doesn&#8217;t flip subscriptions to manual at checkout; it corrupts <em>when</em> renewals fire on existing subscriptions migrated during a narrower window (roughly August through December 2023). The _requires_manual_renewal flag is not directly on the meta keys the Bug 2 fix targeted. Whether the broader backfill issue could have collaterally affected it remains an open question, not a confirmed pathway.</p>



<p><strong>Bug 3 — Re-fetch discarded configured state (fixed in WCS 6.3.0, May 9, 2024).</strong> wcs_create_subscription() ended with a wcs_get_subscription() re-fetch to return a &#8220;fresh&#8221; copy. On HPOS, that re-fetch went through the OrderCache. On high-throughput stores behind database load balancing, it could also hit a read replica that hadn&#8217;t caught up and return false, producing fatal errors — the failure mode that originally motivated the fix. The fix drops the re-fetch entirely and returns the in-memory object.</p>



<p><strong>Bug 4 — Same-gateway switch recovery gap (fixed in WCS 8.6.1, April 23, 2026).</strong> When a subscriber upgraded or downgraded on the same payment gateway, the switcher&#8217;s maybe_set_payment_method_after_switch() recovery path was guarded on gateway-ID change. That guard is partly intentional; it preserves a subscriber&#8217;s deliberate choice to renew manually, but it also prevents subscriptions that had been incorrectly flagged manual by Bugs 1 or 3 from self-healing through a plan change. A recovery gap, not a root cause. It doesn&#8217;t create broken subscriptions on its own. 8.6.1 also fixes a related issue in the other direction: before the patch, changing a subscription&#8217;s payment method or switching the subscription product could silently flip a manual-renewal subscription back to automatic, overriding subscriber intent. Both flows now respect the subscriber&#8217;s existing preference when the merchant has enabled the &#8220;Display the auto renewal toggle&#8221; setting.</p>



<h3 class="wp-block-heading" id="h-how-bugs-1-and-3-combined-to-mint-subscriptions-on-manual"><strong>How Bugs 1 and 3 combined to mint subscriptions on manual</strong></h3>



<p>The &#8220;set to manual at checkout&#8221; outcome needs Bugs 1 and 3 together on an HPOS store. Bug 1 leaves the OrderCache inconsistent after every checkout&#8217;s update_dates() call. Bug 3&#8217;s re-fetch, plus any other code in the same request that reads the subscription back through cache, can return that inconsistent copy. Setters applied in memory after such a read can then be no-op&#8217;d at save time, because the save path diffs against the stale baseline. The net effect is that _requires_manual_renewal is left at its default value of true in the database even though the checkout code intended to clear it.</p>



<p>Critically, fixing either bug alone substantially closed the pathway. A store running WCS 6.1.0 through 6.2.x — Bug 1 fixed, Bug 3 still present — has the dominant source of cache inconsistency closed. The concentrated risk was HPOS stores on WCS <em>below</em> 6.1.0.</p>



<p><strong>Practical exposure window.</strong> HPOS was available as an experimental opt-in from WooCommerce 7.1.0 on November 8, 2022, and became stable and default for new stores in WC 8.2 on October 10, 2023 — which is when adoption actually ramped. Bug 1&#8217;s fix shipped on March 28, 2024. The concentrated window is therefore <strong>roughly October 2023 through March 2024</strong>, with a narrow tail to May 9, 2024 for stores that hadn&#8217;t yet updated to WCS 6.1.0. Any subscription created after the store updated to WCS 6.3.0 (May 2024) or later is not affected.</p>



<h3 class="wp-block-heading" id="h-a-note-on-silent"><strong>A note on &#8220;silent&#8221;</strong></h3>



<p>Once _requires_manual_renewal is incorrectly set to true by Bug 1 or Bug 3, the subscription behaves identically to one that was intentionally configured for manual renewal. At the first renewal date, WC_Subscriptions_Manager::process_renewal() puts the subscription on hold, creates a pending renewal order, and fires the Customer Renewal Invoice email — which is enabled by default on roughly 91.8% of stores, based on the data we have from stores opted in to tracking.&nbsp;</p>



<p>On most affected stores, the subscriber received that email prompting them to pay manually. The merchant typically didn&#8217;t. If the subscriber ignored the invoice, the subscription stayed on-hold and no further renewal events fired until (and unless) they paid, so most affected subscribers received one notification, not a recurring stream. That&#8217;s a real problem, and the one the health check tool will surface,&nbsp; but it&#8217;s a different problem from payments failing with no record anywhere, which is how some of the public framing has landed.&nbsp;</p>



<p>Note: Bug 2 is the exception here: on the narrow cohort it affected, schedule corruption could have prevented the renewal event from firing in the first place, leaving no record. Subscriptions affected by this bug are now surfaced in the health check tool.</p>



<h2 class="wp-block-heading" id="h-a-note-about-manual-renewals"><strong>A note about Manual renewals</strong></h2>



<p>Manual renewal is a supported, intentional payment mode in WooCommerce Subscriptions. Bank transfers, certain APMs like Multibanco, and customer-controlled billing all run on it by design. Some merchants enable it store-wide. Some subscribers choose it when the merchant allows it. In the initial release of the tool, it deliberately will not auto-fix subscriptions — only the merchant has the full store context to tell a bug-caused manual renewal from an intentional one. We are investigating ways to enable auto-healing and/or better “one-click” actions for correcting subscriptions in future iterations of the tool. But we’re erring on the side of caution for this initial release.</p>



<h2 class="wp-block-heading" id="h-what-we-ve-done-since-the-report"><strong>What we&#8217;ve done since the report</strong></h2>



<p>When the public report surfaced, we ran diagnostic queries across the stores we directly manage on our own infrastructure, and we&#8217;ve will reach out to merchants whose stores surfaced potentially-affected subscriptions. If your store is on our hosting and you hear from us about this, that&#8217;s why. Because we have direct access to stores on our managed hosting, we can run this kind of diagnostic and reach out proactively rather than waiting for merchants to use the tool we’re providing.</p>



<p>So far, what we&#8217;ve found on those stores doesn&#8217;t match the scale of impact suggested in the public coverage. However, our focus remains on helping <strong>all</strong> stores get better visibility into the health of their subscriptions, including those not affected by these bugs.</p>



<p>For every merchant running WooCommerce Subscriptions on their own hosting, the Subscriptions Health Check tool is how you get the same visibility on your own store — the subscriptions that <em>could</em> be auto-renewing but aren&#8217;t, for any reason. Our support team is on deck specifically to help you understand what the tool surfaces and decide what to do about it.</p>



<h2 class="wp-block-heading" id="h-what-the-changelog-missed"><strong>What the changelog missed</strong></h2>



<p>The most legitimate question in the public coverage is why Bugs 1–3 weren&#8217;t communicated more clearly when they were fixed. It&#8217;s fair, and it deserves a straight answer.</p>



<p>When those bugs were identified, they were understood internally as High Performance Order Storage (HPOS) compatibility issues — cache invalidation and data sync problems surfaced while implementing HPOS support. We didn&#8217;t draw the line from &#8220;stale cache bug&#8221; to &#8220;subscription could be stuck on manual renewal at checkout.&#8221; The changelog entries were technically accurate, but didn&#8217;t surface the merchant impact.</p>



<p>This wasn&#8217;t a decision to downplay anything. It was a process gap. We&#8217;ve changed how we assess downstream merchant impact when shipping fixes going forward, and how we communicate it. When a bug fix has a plausible downstream effect on merchant revenue or customer-facing behaviour, it should say so in the changelog — and where it warrants, the fix should come with direct outreach to the merchants most likely to be affected.</p>



<h2 class="wp-block-heading" id="h-building-from-here"><strong>Building from here</strong></h2>



<p>The Health Check tool is the first version of what we intend to be an ongoing diagnostic layer for WooCommerce Subscriptions. Surfacing other edge cases that have come up in support tickets over the years are on the roadmap too. The filter architecture is deliberately open-ended so we can keep adding categories.</p>



<p>We wrote this as a tool merchants shouldn&#8217;t ever have needed, but since the &#8220;invisible edge cases&#8221; class of issue is never really going to be empty in any complex plugin, we think it&#8217;s important to give you the scaffolding to catch them. In the meantime, we will continue to rigorously work to squash those edge cases as we discover them in the plugin to the point where the tool is no longer needed.</p>



<p>While the initial version surfaces the subscriptions that might need action from the merchant (we leave that decision up to stores), it does require users to edit the subscription record itself to handle any changes. The next version &#8211; which is already in progress &#8211; will offer in context actions that can be taken to handle those subscriptions right from the tool. We’re taking a more careful approach there because of the various usecases for subscriptions across the ecosystem.&nbsp;</p>



<h2 class="wp-block-heading" id="h-questions"><strong>Questions</strong></h2>



<p>Run the tool now (see <a href="https://woocommerce.com/document/woocommerce-subscriptions-health-check/">documentation here</a>). If anything surfaces that doesn&#8217;t look right, or you have questions about what the results mean for your store, reach out to the<a href="https://woocommerce.com/my-account/contact-support/"> WooCommerce Support team</a> or leave a comment below. Our support team is on deck specifically for this.</p>



<p>If you ran WooCommerce Subscriptions with HPOS enabled between October 2023 and May 2024, the Health Check tool is where to start. If you started using Subscriptions after May 2024, you&#8217;re not affected by the bugs described here — but the tool is still useful for keeping an eye on the ongoing subscription health of your store.</p>
<p>The post <a href="https://developer.woocommerce.com/2026/04/30/subscriptions-health-check/">Giving merchants better visibility into the health of their subscriptions</a> appeared first on <a href="https://developer.woocommerce.com">The WooCommerce Developer Blog</a>.</p>
