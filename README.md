# satisfactory dedicated server hosting: hardware requirements, real costs, and when a bare-metal server beats a $5 game-host plan

A Satisfactory dedicated server keeps your factory running while you sleep, and it lets friends drop in and out without anyone "hosting" the session from their gaming PC. The catch is that Satisfactory is unusually picky about hardware: the official server leans hard on single-core CPU performance, which is exactly the spec that cheap hosting plans cut first. This guide walks through what the server actually needs, what it costs to run one properly, where Sharktech's bare-metal servers fit into that picture, and when a $5–16/month game host is the smarter buy.

> **Quick picks**
> - Most small co-ops (1–4 players): a managed Satisfactory host with 8–16 GB RAM does the job for under $20/month.
> - Big saves, mods, 24/7 megafactories, or a box you also want for other projects: a dedicated machine. Sharktech's bare-metal catalog starts at **$219/month** with 10 Gbps, 300 TB of traffic and 2 TB NVMe included, fully configurable.
> - 👉 [Check Sharktech's current bare-metal configurations and prices](https://bit.ly/SharKtech)

## What the Satisfactory dedicated server actually demands from your hardware

The short version: 8 GB of RAM minimum, a CPU with a single-thread score of 2000 or higher, and about 12 GB of disk for the server files. That's per the official community wiki, and it's worth reading closely because it eliminates a lot of "compatible-looking" hosting.

The wiki's baseline CPU is an Intel i5-3570 or AMD Ryzen 5 3600, and it states plainly that the server "heavily favors high single-core performance." Multiple cores help, but a 36-core Xeon at 2.1 GHz is not automatically better for this game than a 4-core chip at 3.4 GHz. For 1–4 players, 8 GB RAM is fine; the wiki recommends 16 GB once you're running bigger saves or hosting more than 4 players. Storage is modest — 12.4 GB of server files on Windows, roughly 8 GB total on Linux — though save files and mods grow over time, so a 2 TB NVMe is a luxury you'll never complain about.

One warning from the wiki that almost no hosting review mentions: on a VPS, a `kvm64` virtual CPU **won't work**. Satisfactory's dedicated server simply refuses to run on it. This matters because plenty of budget VPS providers ship exactly that CPU model by default. Before renting any virtual server for Satisfactory, you need confirmation that the provider exposes a modern host-CPU model. This single detail disqualifies more cheap VPS plans than price does.

Networking requirements are simple. The server uses port 7777 on both TCP and UDP, so that port must be open or forwarded. Hosting from home means configuring port forwarding or a VPN yourself; a rented datacenter server removes that step entirely.

## Sharktech's plans: a bare-metal catalog, not fixed game-host tiers

Sharktech doesn't sell "Starter/Mid/Pro" game-hosting packages. It sells whole physical servers — every one with a 10 Gbps port, 300 TB of monthly bandwidth and 2 TB of NVMe M.2 storage included — and then lets you customize CPU, RAM and drive layout. The catalog currently spans roughly 56 configurations priced between $219 and $699 per month across five datacenter locations (Chicago, Denver, Las Vegas, Los Angeles, Amsterdam). Here are the configurations most relevant to a Satisfactory server:

| Configuration | CPU | RAM / Storage | Network | Price | Order |
| --- | --- | --- | --- | --- | --- |
| Entry bare metal | Dual Xeon E5-2695v4, 36 × 2.1 GHz | 64 GB / 2 TB NVMe | 10 Gbps / 300 TB | $219/mo | [ Order the $219 entry config](https://bit.ly/SharKtech) |
| Entry, 3.5″ bays | Dual Xeon E5-2695v4, 36 × 2.1 GHz | 64 GB / 2 TB NVMe | 10 Gbps / 300 TB | $229/mo | [ Order the $229 config](https://bit.ly/SharKtech) |
| High-frequency Xeons | Dual Xeon Gold 6246, 24 × 3.3 GHz | 128 GB / 2 TB NVMe | 10 Gbps / 300 TB | $269/mo | [ Order the Gold 6246 config](https://bit.ly/SharKtech) |
| Gold 6248 | Dual Xeon Gold 6248, 40 × 2.5 GHz | 128 GB / 2 TB NVMe | 10 Gbps / 300 TB | $259/mo | [ Order the Gold 6248 config](https://bit.ly/SharKtech) |
| Gold 6248, all-NVMe | Dual Xeon Gold 6248, 40 × 2.5 GHz | 128 GB / 2 TB U.2 NVMe | 10 Gbps / 300 TB | $289/mo | [ Order the all-NVMe config](https://bit.ly/SharKtech) |
| Single EPYC | AMD EPYC 7702P, 64 × 2 GHz | 128 GB / 2 TB NVMe | 10 Gbps / 300 TB | $499/mo | [ Order the EPYC 7702P config](https://bit.ly/SharKtech) |
| Dual EPYC | Dual AMD EPYC 7702, 128 × 2 GHz | 128 GB / 2 TB NVMe | 10 Gbps / 300 TB | $699/mo | [ Order the dual-EPYC flagship](https://bit.ly/SharKtech) |

All prices are monthly, USD; annual billing works out to exactly 12× the monthly rate with no extra discount. Two notes worth flagging before you click anything. First, for Satisfactory specifically, the **Gold 6246 at 3.3 GHz is the most interesting chip in that table** — the game wants clock speed more than core count, so paying $269 for 24 fast cores beats paying $259 for 40 slower ones. Second, Amsterdam runs roughly $40–50/month more than US locations for identical hardware, so if your group is EU-based but budget-sensitive, a Chicago or Denver box with good routing can still be the better deal.

Every server also includes Sharktech's in-house DDoS protection at up to 60 Gbps for free, upgradeable to a 100 Gbps cloud-based shield. For a public server with a known IP, that's not trivia — game servers get attacked, and budget hosts frequently null-route attacked IPs until the storm passes.

Sharktech also sells VPS plans, which are worth a look if you want to experiment cheaply:

| VPS Plan | CPU | RAM | Price |
| --- | --- | --- | --- |
| XS | 2 cores | 4 GB | $3.98/mo |
| S | 4 cores | 8 GB | $6.98/mo |
| M | 8 cores | 16 GB | $12.98/mo |
| L | 16 cores | 32 GB | $24.99/mo |
| XL | 32 cores | 64 GB | $48.98/mo |

Before grabbing the S plan for 8 GB of RAM, re-read the `kvm64` paragraph above and confirm with the provider that the VPS exposes a qualifying host CPU. If it doesn't, the money is wasted regardless of how good the price looks.

## The real cost of running Satisfactory on a dedicated server

Nobody in the top search results does this math honestly, so here it is. A $219/month Sharktech server costs **$2,628 in the first year** and the same in every subsequent year, since annual billing is just 12× monthly. A Gold 6246 at $269 runs $3,228/year. There's no setup fee and stock systems ship within 24 hours (custom builds take 1–2 weeks depending on parts), but there is no price drop after month one.

Set that against managed game hosts: a 16 GB Satisfactory plan with automatic backups and DDoS protection runs about £4.80/month, and an 8 GB plan at another host is $16/month. Over a year that's roughly $75–230 versus $2,600+. For a four-person co-op, the dedicated server is a spectacularly bad deal.

So why does the math ever work? Three scenarios:

1. **You need more than one thing from the machine.** A bare-metal box with 64–128 GB RAM and 2 TB NVMe can run the Satisfactory server, a Minecraft server (Sharktech's own promos have pitched high-clock dual Xeons at exactly this use case), a Mumble voice server, and a media server side by side. Split four ways among a serious group, $219/month stops being absurd.
2. **Your save is a monster.** Late-game megafactories with thousands of machines and heavy modding are where 8 GB game-host plans start choking. If your save already struggles on a shared host, dedicated hardware with a high-clock CPU is the actual fix.
3. **You run a public community server** where downtime, DDoS null-routing and noisy neighbors directly cost you players.

If none of those describe you, stop reading the dedicated server tables and rent a managed plan. Seriously — that's the correct answer, and any review pretending otherwise is optimizing for its affiliate link.

## How Sharktech compares to the game-host plans you'll see first

For calibration, here's what the currently active competition looks like on verified pricing. No links here on purpose — the goal is context, not a shopping list.

| Provider | Satisfactory-relevant plan | Hardware | Price | Notable policies |
| --- | --- | --- | --- | --- |
| EUGameHost | Starter: up to 20 players | 16 GB DDR4, Xeon 3.8 GHz+ / Ryzen 9 7950X, NVMe, 10 Gbps | £4.80/mo | 48-hour money-back guarantee; London & Dallas; ~60-second deployment |
| EUGameHost | Mid: up to 64 players | 24 GB DDR4 | £9.60/mo | Same inclusions |
| EUGameHost | Top: up to 128 players | 32 GB DDR4/DDR5 | £25.60/mo | Same inclusions |
| Solace Servers | Small Factory: 1–2 players | 4 GB RAM, NVMe, DDoS protection | $8/mo | No contract, cancel anytime; Toronto & Virginia |
| Solace Servers | Megabase: 4+ players | 8 GB RAM | $16/mo | Same inclusions |
| IONOS | Scenario-based: 2 players → VPS XL; 3–8 → VPS XXL; 8+ → dedicated | Varies | Not published here | 30-day free cloud server trial |
| Sharktech | Bare-metal catalog | 36–128 cores, 64–128 GB, 2 TB NVMe, 10 Gbps / 300 TB | $219–699/mo | No refunds (see below); 5 datacenter locations |

The managed hosts win on convenience, price and one thing people underestimate: the Satisfactory Mod Manager ecosystem, where EUGameHost offers one-click mod packs and browser-based config editing. Sharktech gives you a raw root server — you install SteamCMD, the server binary and any panel yourself. That's genuinely better for modding freedom and multi-game use, and genuinely worse if you wanted to click one button.

## Setting up the server on your Sharktech machine

Setup is a standard SteamCMD job. On Linux, one command pulls the server files (App ID 1690800):


steamcmd +force_install_dir ~/SatisfactoryDedicatedServer +login anonymous +app_update 1690800 validate +quit


On Windows, the same line works with the SteamCMD executable path prefixed. The wiki recommends Windows Server as the developer-preferred option — Windows 10/11, Server 2016/2019/2022 and Debian/Ubuntu are all supported. After install, open port 7777 on both TCP and UDP in the firewall, launch the server, and clients from both Steam and Epic can connect to it; the download source of the server binary doesn't restrict who can join. Add `-beta experimental` to the SteamCMD command if you want the experimental branch.

Where a dedicated box changes the experience versus a game host: you get full root, so mods install however you like, backups run on whatever schedule you script, and the same machine can host other services. The trade is that you're the admin. Nothing auto-deploys in 60 seconds; stock hardware targets delivery within 24 hours, and then it's on you.

One thing to know before any purchase at Sharktech: there's **no free trial and no refund guarantee**. All payments, including monthly fees, are non-refundable, and billing disputes must be raised within 30 days of the invoice, resolved (if won) as account credit rather than cash. Payment options include credit card, PayPal, bank wire, Western Union and Alipay. Given that, 👉 [review the full configuration catalog and current pricing before committing](https://bit.ly/SharKtech) — and be sure about the plan, because the money doesn't come back.

## FAQ

**How many players does a Satisfactory dedicated server support?**
Officially, Satisfactory's multiplayer is designed and optimized for up to 4 players. Worlds with more than 4 can be configured and hosts advertise plans for 20–128 "players," but the developer doesn't guarantee performance beyond 4 — player count is really a proxy for how much factory exists in the world.

**What port does the Satisfactory server use?**
Port 7777, and it must be open for both TCP and UDP. Miss one protocol and clients will fail to connect in confusing ways.

**Is a VPS good enough for Satisfactory?**
Sometimes, but check the virtual CPU model first — a `kvm64` CPU will not run the dedicated server at all. You also want strong single-core performance (single-thread rating 2000+) and 8–16 GB RAM.

**How fast is a Sharktech server delivered?**
In-stock configurations target delivery within 24 hours. Custom builds (different CPU, RAM, drive layout, network) take 1–2 weeks depending on part availability.

**Does Sharktech include DDoS protection?**
Yes — every server gets automatic protection against attacks up to 60 Gbps at no charge, with an optional upgrade to 100 Gbps of cloud-based protection.

## Where to land: the decision, in one paragraph

Running a factory for two to four friends → a managed plan from EUGameHost (£4.80) or Solace ($8–16) is the right tool, and paying Sharktech prices for it would be silly. Testing whether a big community server is worth the effort → try IONOS's 30-day free cloud server, then graduate if it sticks. Running a megafactory, a modded world, multiple game servers, or a public community that can't afford null-routing during an attack → a high-clock dedicated machine is the actual fix, and the Gold 6246 config at 3.3 GHz is the smart pick from Sharktech's table rather than the cheapest one. Whenever you've settled on the dedicated route, 👉 [order your Sharktech bare-metal server and keep your factory running around the clock](https://bit.ly/SharKtech) — just double-check the location dropdown during configuration, since stock and pricing differ per datacenter and Amsterdam costs more for identical hardware.
