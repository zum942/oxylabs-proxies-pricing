# oxylabs residential proxies: Real Plan Prices, the 50GB Pay-As-You-Go Cap, and When a Pay-Per-Request API Fits Better

Most pages about **oxylabs residential proxies** lead with the same numbers: a massive IP pool, global coverage, a high success rate. Those numbers are real, but they skip the details that actually determine whether you should buy: the Pay As You Go plan costs $8/GB and stops working past 50GB a month, the entry subscription runs about $7.75/GB, and the refund window is three days with a traffic cap attached. This guide goes through Oxylabs' residential proxy plans as listed on their own pricing page, the restrictions that can disqualify your targets entirely, and a comparison with ScraperAPI, a pay-per-request alternative that bills differently and suits a different kind of project.

> **Quick take:** Oxylabs charges $8/GB with no commitment (capped at 50GB/month), or $99/month for 13GB on the Micro plan. If you'd rather pay per request and let someone else handle proxies, CAPTCHAs, and retries, [👉 check ScraperAPI's plans and start with 1,000 free credits](https://www.scraperapi.com/?fp_ref=coupons) — and the 7-day trial with 5,000 credits requires no credit card.

## What Oxylabs residential proxies actually cost

Oxylabs prices residential proxies by traffic, billed monthly. Their dedicated residential pricing page currently lists three self-service options, plus custom and enterprise arrangements above that:

| Plan | Monthly traffic | Price | Effective rate | Commitment |
| --- | --- | --- | --- | --- |
| Pay As You Go | Up to 50GB | $8/GB | $8/GB | None, non-refundable |
| Micro | 13GB | $99 + VAT/month | ~$7.75/GB | Monthly |
| Starter | 40GB | $300 + VAT/month | ~$7.50/GB | Monthly |
| Enterprise / high-volume | 1TB+ | Varies by use case | Lower per GB | Custom terms |

Every plan includes unlimited concurrent sessions, free geo-targeting, 24/7 support, and a dedicated account manager. Sticky sessions, flexible rotation, 3 proxy users, and 10 whitelisted IPs are bundled at no extra charge. Annual billing takes 10% off any plan, but there's a catch: you have to contact sales to arrange it, so the discount isn't available through self-serve checkout.

Two details worth flagging. First, per-GB pricing drops substantially at higher volumes — Oxylabs' site displays larger monthly tiers where the effective rate falls toward the $4/GB range and lower at terabyte scale, though the pricing page notes that plans above 1TB can vary by use case, so the exact numbers need a sales quote. Second, listed prices exclude VAT, so European buyers should budget for tax on top of the quoted figures.

## The limits that most comparisons leave out

The Pay As You Go plan has a hard monthly ceiling: **50GB of traffic per month**, and unused GBs reset to zero after each month. Oxylabs' own FAQ says it directly — if you consistently need more than 50GB, they recommend switching to a subscription. For a short one-off project that stays under the cap, PAYG works fine. For anything sustained, it's a temporary arrangement.

The refund policy is tighter than most people expect. Self-service subscriptions are refundable, but only if you meet all of these conditions:

- The refund request comes within **3 calendar days** of your first payment
- You've used no more than **20% of the traffic** on Regular plans (10% on Enterprise plans)
- Your account isn't suspended for a breach of the subscription agreement
- You haven't charged back the payment or claimed a refund before

And Pay As You Go purchases are non-refundable, full stop. Combined with the monthly reset, that means unspent PAYG credit quietly disappears — you can't bank it or get it back.

The free trial has a gate too. Oxylabs offers a 7-day free trial, but it's only available to accounts with **verified company registration**. Individual developers and hobbyists can't just sign up and test; the accessible option for them is the $5 welcome credit on the paid side.

## The target list that can end your project before it starts

Oxylabs blocks a specific set of targets across its residential network as an anti-abuse measure. Per their pricing page FAQ, the restricted list includes — but isn't limited to:

- All Apple domains, including iTunes and App Stores
- Entertainment platforms like Netflix and PlayStation
- Banking and other financial institutions
- Some Google domains
- Government websites
- Streaming and ticketing sites
- LinkedIn and mailing services

This applies regardless of which plan you buy. If your target site sits anywhere near that list, check first: Oxylabs' 24/7 live chat or their support email can confirm whether your specific use case is allowed. Getting that confirmation in writing before subscribing to a monthly plan is the cheapest insurance available here.

## What the infrastructure itself delivers

On raw specs, the residential pool is strong. Oxylabs' product page advertises 175M+ IPs across 195+ countries, with an average 99.95% success rate and 0.6s average response time — though their own pricing page quotes a more conservative pool size of 100M+ IPs covering 195 locations, so the exact pool figure depends on which page you read. Independent testing cited on the product page (conducted by Proxyway) measured a 99.82% success rate and 0.41s response time against three competitors — the strongest of the four on both counts, though the page's own disclaimer notes these figures were recorded at the time of testing.

Protocol and targeting options matter for technical buyers:

- HTTP(S), HTTP3, and SOCKS5 support, running on the QUIC protocol
- Geo-targeting down to country, city, state, ZIP code, coordinates, and ASN — all free
- Unlimited concurrent sessions with no connection limits
- IPs filtered by latency, bandwidth, and scraping history, with adaptive adjustment

Integration is a standard gateway setup with credentials, and Oxylabs publishes code examples for Python, Node.js, PHP, Go, and other languages on GitHub. If you already run a scraping stack, swapping in better IPs is a configuration change, not a rewrite.

The trade-off is that this is infrastructure. Rotation logic, retries, header management, and CAPTCHA fallbacks stay on your side, and every failed request burns traffic you paid for — which matters more on JavaScript-heavy pages, where a single render can pull megabytes.

## ScraperAPI: a different billing model for the same problem

ScraperAPI approaches web scraping from the other end. Instead of selling proxy bandwidth, it exposes an API endpoint that handles proxy rotation, JS rendering, CAPTCHA and anti-bot detection, and automatic retries internally. You pay in **API credits per request**, not per GB — so a failed render that would eat your Oxylabs traffic budget costs nothing extra here if the service retries it.

Here's the plan lineup as listed on ScraperAPI's official pricing page:

| Plan | Credits/month | Monthly | Annual (10% off) | Concurrency | Purchase |
| --- | --- | --- | --- | --- | --- |
| Free | 1,000 | $0 | — | 5 threads | [ Sign up free](https://www.scraperapi.com/?fp_ref=coupons) |
| Hobby | 100,000 | $49 | $44.10/mo | 20 threads | [ Get Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | 1,000,000 | $149 | $134.10/mo | 50 threads | [ Get Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | 3,000,000 | $299 | $269.10/mo | 100 threads | [ Get Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | 5,000,000 | $475 | $427.50/mo | 200 threads | [ Get Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | 10,500,000 | $975 | $877.50/mo | 300 threads | [ Get Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | 21,500,000 | $1,975 | $1,777.50/mo | 500 threads | [ Get Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | 22M+ | Custom | — | 500+ threads | [ Contact sales](https://www.scraperapi.com/?fp_ref=coupons) |

Every plan includes JS rendering, premium residential and mobile IPs, JSON auto-parsing, custom sessions, custom headers, desktop and mobile user agents, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. Higher tiers add advanced bypassing, parsing and structured data APIs, DataPipeline, full crawler access, and pay-as-you-go overflow. There's also a 7-day trial with 5,000 credits that doesn't require a credit card, and you can cancel a subscription anytime from the dashboard without being charged.

Geotargeting on lower tiers is limited to US and EU regions; country-level targeting starts on the Business plan and up.

## Per-GB vs per-request: where each model wins

Credit costs aren't uniform. A standard page costs 1 credit, but ScraperAPI prices hard targets differently: Amazon costs 5 credits, Google and Bing (including subdomains) cost 25, and LinkedIn costs 30. Requests that get past protection like Cloudflare, Datadome, or PerimeterX add 10 credits each. You can cap any single request with a `max_cost` parameter, and the dashboard's Domain Cost Estimator shows exact per-domain costs — worth running on your real target URLs before you pick a tier, since a project that looks like 50,000 requests can quietly become 300,000 credits once 25-credit Google endpoints enter the mix.

That pricing structure changes the comparison with Oxylabs in specific ways:

- **JavaScript-heavy sites favor per-request billing.** On a per-GB plan, every script, image, and retry consumes traffic. A bloated render that fails and repeats burns you twice. On ScraperAPI, the same page costs the same credits whether it's 50KB or 2MB.
- **Google scraping is expensive on both models.** Google sits at 25 credits per request on ScraperAPI, and "some Google domains" are on Oxylabs' restricted list. For SERP work specifically, ask either vendor about dedicated SERP products before committing to general-purpose plans.
- **Tight, high-volume pipelines favor raw proxies.** If you're pulling millions of lightweight pages with careful request control, Oxylabs' discounted high-volume rates undercut per-request pricing — especially for 1–5 credit targets.

A rough back-of-envelope comparison, using a hypothetical 1MB average page: at PAYG's $8/GB, that works out to roughly $8 per 1,000 standard pages (your real number depends entirely on page weight and failed-request overhead). Against that, ScraperAPI's Hobby plan at $49 for 100,000 credits comes to roughly $0.49 per 1,000 standard requests. These are illustrative estimates, not official figures — but the direction holds for sub-100GB workloads, and the API model also removes the engineering overhead of managing rotation yourself.

One operational note on ScraperAPI: hitting your concurrency limit returns a 429 with no charge — the request is refused, not queued. Running out of credits pauses scraping by default, but Hobby through Professional offer opt-in auto-upgrade to the next plan, and Scaling and above support pay-as-you-go overflow at a fixed per-credit rate with a monthly spending cap you set. Nothing stops mid-month without a warning path.

## FAQ

**Is there a free way to test Oxylabs residential proxies?** Two options, both limited: a $5 welcome credit for new users, and a 7-day free trial that requires verified company registration. Individual developers without a registered company are limited to the welcome credit. ScraperAPI's free plan — 1,000 credits, 5 concurrent threads — is the more accessible test path, and [👉 you can sign up for it here](https://www.scraperapi.com/?fp_ref=coupons).

**Does Oxylabs residential proxies support SOCKS5?** Yes. The residential pool supports HTTP, HTTPS, SOCKS5, and HTTP3 protocols, with sticky sessions and flexible rotation included in every plan.

**Which ScraperAPI plan covers 100,000 requests a month?** The Hobby plan: $49/month for 100,000 credits and 20 concurrent threads, or $44.10/month billed annually. Remember that's 100,000 *standard* requests — target Google at 25 credits each and the same allowance covers only about 4,000 requests.

**Can I get a refund from Oxylabs if I change my mind?** On self-service subscriptions, yes, if you request within 3 calendar days of first payment and have used under 20% of your traffic (10% on Enterprise plans), among other conditions. Pay As You Go purchases are non-refundable regardless.

## Picking based on your situation

- Running your own scraping stack at serious volume, needing city or ZIP-level targeting on raw connections, or requiring SOCKS5: Oxylabs' higher tiers are priced for exactly this, and the $5 welcome credit lets you validate the pool before committing to a monthly plan.
- A developer or small team scraping a handful of sites: start with ScraperAPI's free 1,000 credits, test your real targets, and move to Hobby ($49) or Startup ($149) if the numbers hold. The cancel-anytime policy and the no-card 7-day trial make this the lower-risk starting point by a wide margin.
- Mixed workloads: plenty of teams run both — an API for the high-friction, JS-heavy targets, raw proxies for the custom pipelines. That's a legitimate architecture, not indecision.

Two checks before you spend anything: confirm your target domains aren't on Oxylabs' restricted list (get confirmation from their support in writing if you're unsure), and whichever side of the per-GB vs per-request line you land on, price your actual workload — not the headline rate. [👉 Start with ScraperAPI's free plan and test your real targets](https://www.scraperapi.com/?fp_ref=coupons) before comparing monthly plans.
