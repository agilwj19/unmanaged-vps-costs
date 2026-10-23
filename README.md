# unmanaged vps server: what you actually administer, what each plan really costs, and how to pick a China-route box

An unmanaged VPS gives you root access and a running virtual machine, then gets out of the way. You install the stack, patch the kernel, configure the firewall, and own every outage at 2 a.m. In exchange you pay less and keep control that managed hosting never hands over.

That trade is well understood. The part most guides skip is that "unmanaged" covers a wide price range, and the gap between two unmanaged boxes with near-identical specs usually comes down to something absent from the CPU/RAM column: the network route to your users, the port speed, and whether the provider quietly changed a plan's disk size while leaving the name alone. This walkthrough covers what you actually administer, where cheap plans stop making sense, and how GoMami's lineup looks once you line the plans up honestly — including a couple of naming traps that are easy to miss at checkout.

> **Quick take:** if most of your visitors are in mainland China and you want the cheapest plan with a proper three-carrier return route, the Hong Kong Pulse Mini (2 vCPU / 4GB / 60GB NVMe / 1TB / 1Gbps) at **$59/month** is the sensible default. Serving Japan or Singapore instead, the Tokyo or Singapore Nano at **$29/month** does the job with a smaller traffic allowance. Windows only works on the Pro and Ultra tiers.
>
> 👉 [See GoMami's current VPS plans and live stock](https://bit.ly/Gomami)

## What does "unmanaged" actually put on your plate?

The provider owns the hypervisor, the physical host and the network. You own the guest operating system and everything running on it. That is the whole boundary, and it is the same at every unmanaged host.

In practice that means root or Administrator access, your choice of distro, and full responsibility for the OS, firewall, application stack and backup policy. GoMami runs KVM, which gives each instance its own virtual CPU, RAM, disk and kernel-level isolation — standard for this price class. Common images boot out of the box at providers in this segment; anything unusual is on you to install.

GoMami layers a few extras on top of the baseline: daily automated backups to AWS S3 on every plan, free installation, NVMe storage across the catalogue, and DDoS mitigation. Read the DDoS wording carefully. The homepage advertises "up to 600 Gbps mitigation capacity," while the documentation describes protection as best-effort by default with 600 Gbps scrubbing available as an upgrade. Plan your budget around the second version.

The control panel is VirtFusion. It shows server name, IP, billing cycle, expiry date and network type, plus live CPU, memory and traffic graphs. Nothing exotic — you will still be doing most of your work over SSH.

## Who should not buy an unmanaged VPS at all?

If you have no intention of touching a terminal, skip this category entirely. The savings disappear the first time you spend a weekend rebuilding a broken nginx config, and a managed plan costing a few dollars more is cheaper than your time.

There is a second group that should close the tab: anyone whose entire budget is five dollars a month. This category prices network quality more than compute. GoMami's entry plans sit at $29/month, and the Hong Kong hardware people actually want for China-facing sites starts at $59. Budget-tier hosts sell usable boxes for less — just on routes that were never optimised for Chinese carriers.

The fit is elsewhere: developers running a container or two, agencies hosting client sites for a Chinese audience, game server admins who care about latency, and anyone moving off shared hosting who is comfortable in SSH. If you can install Docker and read the output of `systemctl status`, you qualify.

## GoMami's full plan list

GoMami splits its catalogue by hardware platform first and location second. The same plan names — Mini, Air, Pro — appear on several platforms with different specs and prices, so platform matters as much as plan name.

### Hong Kong Peak X5 (AMD Ryzen 9 9950X, up to 5.7GHz)

The three plans on GoMami's homepage. This is the single-thread performance line, aimed at game servers and latency-sensitive applications.

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| Peak X5 Mini | 2 / 4GB / 40GB | 1000GB / 2Gbps | $59/mo | [Order Peak X5 Mini](https://gomami.io/aff.php?aff=415&pid=1) |
| Peak X5 Air | 4 / 8GB / 60GB | 2000GB / 2Gbps | $99/mo | [Order Peak X5 Air](https://gomami.io/aff.php?aff=415&pid=2) |
| Peak X5 Pro | 6 / 16GB / 80GB | 5000GB / 5Gbps | $199/mo | [Order Peak X5 Pro](https://gomami.io/aff.php?aff=415&pid=3) |

### Hong Kong Pulse (AMD EPYC 7763, up to 3.5GHz)

Five plans, all tagged "China Mainland Optimized Pro" on the store page. Only Pro and Ultra are marked Windows-ready.

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| Pulse Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $49/mo | [Order Pulse Nano](https://gomami.io/aff.php?aff=415&pid=26) |
| Pulse Mini | 2 / 4GB / 60GB | 1000GB / 1Gbps | $59/mo | [Order Pulse Mini](https://gomami.io/aff.php?aff=415&pid=4) |
| Pulse Air | 4 / 8GB / 80GB | 2000GB / 1Gbps | $119/mo | [Order Pulse Air](https://gomami.io/aff.php?aff=415&pid=5) |
| Pulse Pro | 8 / 16GB / 100GB | 5000GB / 3Gbps | $269/mo | [Order Pulse Pro](https://gomami.io/aff.php?aff=415&pid=6) |
| Pulse Ultra | 12 / 32GB / 300GB | 10000GB / 3Gbps | $499/mo | [Order Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=25) |

### Hong Kong Turin (AMD EPYC 9575F, Zen 5, up to 5GHz)

PCIe Gen5 U.2 SSDs and DDR5-6400 memory. Pro and Ultra support Windows.

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| Turin Mini | 2 / 4GB / 100GB | 1000GB / 2Gbps | $69/mo | [Order Turin Mini](https://gomami.io/aff.php?aff=415&pid=14) |
| Turin Air | 4 / 8GB / 140GB | 2000GB / 2Gbps | $129/mo | [Order Turin Air](https://gomami.io/aff.php?aff=415&pid=15) |
| Turin Pro | 6 / 16GB / 180GB | 5000GB / 5Gbps | $299/mo | [Order Turin Pro](https://gomami.io/aff.php?aff=415&pid=16) |
| Turin Ultra | 12 / 32GB / 220GB | 10000GB / 5Gbps | $599/mo | [Order Turin Ultra](https://gomami.io/aff.php?aff=415&pid=22) |

### Japan Pulse (EPYC 7773X / 7K83)

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| JPN Pulse Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $29/mo | [Order JPN Pulse Nano](https://gomami.io/aff.php?aff=415&pid=13) |
| JPN Pulse Mini | 2 / 4GB / 60GB | 1000GB / 1.5Gbps | $49/mo | [Order JPN Pulse Mini](https://gomami.io/aff.php?aff=415&pid=10) |
| JPN Pulse Air | 4 / 8GB / 80GB | 2000GB / 1Gbps | $89/mo | [Order JPN Pulse Air](https://gomami.io/aff.php?aff=415&pid=11) |
| JPN Pulse Pro | 8 / 16GB / 100GB | 5000GB / 3Gbps | $169/mo | [Order JPN Pulse Pro](https://gomami.io/aff.php?aff=415&pid=12) |
| JPN Pulse Ultra | 12 / 32GB / 300GB | 10000GB / 3Gbps | $338/mo | [Order JPN Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=24) |

### Singapore Pulse (EPYC 7663)

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| SIN Pulse Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $29/mo | [Order SIN Pulse Nano](https://gomami.io/aff.php?aff=415&pid=21) |
| SIN Pulse Mini | 2 / 4GB / 60GB | 1000GB / 1Gbps | $49/mo | [Order SIN Pulse Mini](https://gomami.io/aff.php?aff=415&pid=17) |
| SIN Pulse Air | 4 / 8GB / 80GB | 2000GB / 1Gbps | $89/mo | [Order SIN Pulse Air](https://gomami.io/aff.php?aff=415&pid=18) |
| SIN Pulse Pro | 8 / 16GB / 100GB | 5000GB / 3Gbps | $169/mo | [Order SIN Pulse Pro](https://gomami.io/aff.php?aff=415&pid=19) |
| SIN Pulse Ultra | 12 / 32GB / 300GB | 10000GB / 5Gbps | $338/mo | [Order SIN Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=23) |

### Los Angeles Pulse (EPYC 7K62)

The newest location, with the largest traffic allowances: the LAX Nano gets 1TB where the Asian Pulse Nano gets 500GB.

| Plan | vCPU / RAM / NVMe | Traffic / port | Price | Order |
| --- | --- | --- | --- | --- |
| LAX Pulse Nano | 2 / 2GB / 40GB | 1TB / 1Gbps | $29/mo | [Order LAX Pulse Nano](https://gomami.io/aff.php?aff=415&pid=27) |
| LAX Pulse Mini | 2 / 4GB / 60GB | 2TB / 1Gbps | $59/mo | [Order LAX Pulse Mini](https://gomami.io/aff.php?aff=415&pid=28) |
| LAX Pulse Air | 4 / 8GB / 80GB | 4TB / 2Gbps | $129/mo | [Order LAX Pulse Air](https://gomami.io/aff.php?aff=415&pid=29) |
| LAX Pulse Pro | 6 / 16GB / 100GB | 8TB / 3Gbps | $259/mo | [Order LAX Pulse Pro](https://gomami.io/aff.php?aff=415&pid=30) |
| LAX Pulse Ultra | 12 / 32GB / 300GB | 15TB / 5Gbps | $599/mo | [Order LAX Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=31) |
| LAX Pulse Titan | 12 / 32GB / 600GB | 30TB / 10Gbps | $999/mo | [Order LAX Pulse Titan](https://gomami.io/aff.php?aff=415&pid=32) |

There is also a dedicated-server line, **HKG Forge**, running AMD EPYC 7663 with 56 cores and 112 threads on the same CN2 / 9929 / CMIN2 routing. The Forge Mini lists 128GB RAM, 960GB NVMe and 10TB traffic at 2Gbps for $399/month plus a one-time $68 setup fee. That is a bare-metal product, not a VPS, and it is the option to look at only once a single virtual machine genuinely cannot carry the workload.

👉 [Browse the Hong Kong Pulse, Peak X5 and Turin plan pages together](https://bit.ly/Gomami)

## The naming trap: same plan name, different machine

"Pro" does not mean one thing at GoMami. On the Hong Kong Pulse line, Pro is 8 vCPU with a 3Gbps port for $269. On Peak X5, Pro is 6 vCPU with a 5Gbps port for $199. You pay $70 less and get two fewer cores, because Peak X5 is selling clock speed and port bandwidth instead of core count.

Per-core the two land close: about $33.6 per vCPU on Pulse Pro versus $33.2 on Peak X5 Pro. The real question is which resource your workload is short of. MySQL InnoDB and Redis benefit from single-thread latency, and Ryzen's 5.7GHz boost is why that line exists. A container host running twenty small services wants cores, and Pulse Pro wins on that count. Air is where the two lines are closest in shape — 4 vCPU / 8GB on both, 60GB versus 80GB of disk, $99 versus $119, and the extra $20 buys 2Gbps instead of 1Gbps plus the faster clock.

Turin sits above both. It costs $10 more than Peak X5 Mini and $10 more than Pulse Mini at the entry point, and what that buys is Zen 5 with Gen5 SSDs, DDR5-6400 and 100GB of disk instead of 40GB. If you run a database that is genuinely disk-bound, the $69 plan is money well spent. For a brochure site it is $10 a month spent on hardware you will never stress.

> **Watch the specs, not the name.** The homepage still lists an EPYC Mini at $39/month with 40GB of disk. The Pulse Mini in the store is $59/month with 60GB. Both are labelled "Mini," both run EPYC silicon, and they are not the same product. Confirm vCPU count, disk and port speed on the configure page before you pay.

## Traffic, ports and the billing details worth checking

Hong Kong plans are billed on one-way traffic with one IPv4 address per instance. IPv6 is not mentioned on the plan pages, so if your stack assumes dual-stack, ask before ordering.

When you run out of traffic, GoMami sells top-up packs that are added to the instance's monthly quota immediately. What the documentation does not spell out is whether an exhausted quota throttles the port or suspends the server. The site's own FAQ lists "what happens when traffic runs out" as a question without a published answer — the FAQ is largely a list of questions GoMami has not answered in public. Trial availability, IP Transit purchases, data handling and team or nonprofit discounts are all listed there without answers. If any of those affect your decision, open a ticket first.

The refund position is similarly thin. One community write-up mentions a 24-hour no-questions refund, but no refund policy appears on the official pages, so treat that as unconfirmed until support puts it in writing.

Everything else about the order flow is documented clearly. Switching to a longer billing cycle usually lowers the monthly price, and the order summary updates live as you change it. Payment goes through card, Stripe Alipay, crypto or account credit. Deployment starts automatically once payment clears and typically finishes within a few minutes, with the IP address and login credentials arriving by email. The checkout has a promo code field; codes circulate in third-party reviews, but none are published officially, so verify any code before relying on the discount.

👉 [Check the Hong Kong plan list and pick a billing cycle](https://bit.ly/Gomami)

## What the China-route premium actually buys

GoMami's pitch rests on three claims: mainland China round-trip latency under 50ms, three-carrier optimisation, and premium return routing. Asia nodes use China Telecom's CN2, China Unicom's AS9929 and China Mobile's CMIN2 on the return path. The Los Angeles node runs premium routing in both directions across all three carriers, which makes it the most heavily optimised route in the lineup and the reason its traffic allowances are larger.

The claimed sub-50ms figure is a vendor claim. Independent testing is thinner but points the same way. DigVPS measured a Hong Kong Turin instance at 40.4ms latency with 2.16 Gbps sustained throughput to Singapore and 1.76 Gbps to Shenzhen Telecom, with 893 Mbps on the return leg. The same testing outfit rated Hong Kong and Los Angeles at E2 and Japan and Singapore at E3, and its published comment described GoMami as well suited to website hosting with solid performance and reasonable configuration.

That is where the money goes. A $5 box in Frankfurt will serve a Berlin visitor faster than anything here, and if your audience is European or American, paying this premium is waste. If a 200ms swing on the checkout page costs you conversions in Shanghai, the arithmetic points the other way.

Against the budget tier, GoMami loses badly on specs per dollar. Hetzner lists unmetered bandwidth under fair use with no overage fee. Kimsufi and PulseHeberg advertise 1Gbps unmetered ports. BuyVM offers a 10Gbps burst port under a reasonable-use policy. Regional listings from earlier in 2026 put a DigitalOcean 1GB droplet at roughly ₹500/month and a Vultr Bangalore 2GB plan at around ₹1,466/month, both unmanaged. Every one of those costs less than GoMami's entry plan. None of them sells you a three-carrier return route to mainland China.

👉 [Compare the EPYC, Ryzen and Turin plans at current prices](https://bit.ly/Gomami)

## Which plan to actually order

Match the plan to the audience and the workload, and stop at the first one that covers it.

- **Mainland Chinese visitors, general web or app hosting** → Hong Kong Pulse Mini at $59/month. Same three-carrier return route as the premium lines, 4GB of RAM, 1TB of traffic.
- **Japan or Singapore audience, small site or proxy** → the $29 Nano in either location. Expect 500GB of traffic, not a terabyte.
- **US box that still needs decent China routing** → LAX Pulse Nano at $29 with 1TB, or the $59 Mini if you need 2TB.
- **Game servers or latency-sensitive single-thread work** → Peak X5 Mini at $59, or Peak X5 Pro at $199 if you need the 5Gbps port.
- **Database work where disk throughput is the bottleneck** → Turin Mini at $69.
- **Many small services, core count over clock speed** → Pulse Pro at $269 for 8 vCPU, or Pulse Ultra at $499 for 12.
- **Windows** → only Pulse Pro, Pulse Ultra, Turin Pro and Turin Ultra are marked Windows-ready.
- **Testing the waters** → buy monthly on the smallest plan that runs your stack, confirm the route behaves, then move to a longer cycle for the discount.

Two things to settle before checkout: the exact vCPU count, disk and port speed on the plan you selected, since names repeat across platforms, and what happens when the traffic quota runs out. Both are answerable on the configure page or by asking support. Neither is worth guessing.

One last note on the Pulse Ultra: the store cart lists it at 12 vCPU with a 3Gbps port, while at least one third-party listing shows 16 vCPU and 5Gbps at the same $499. Check the configure page before buying, because that difference changes which plan makes sense for a container host.

👉 [Start with the GoMami plan that matches your workload](https://bit.ly/Gomami)
