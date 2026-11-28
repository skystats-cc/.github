<div align="center">

# SkyStats.cc

**Money tracking for Hypixel SkyBlock.**

Track your purse, bank and co-op over time, compare money-making methods, and follow the whole bazaar.

[Website](https://skystats.cc) · [API](https://api.skystats.cc) · [Report a bug](https://github.com/skystats-cc/server/issues)

</div>

---

## What it does

- **Money-making methods (MMMs).** Each method is its own module, so we can start simple and add more over time.
- **Co-op tracking.** See every active member's purse, personal bank and SkyBlock XP, plus the shared bank. You can also see who is online and grinding.
- **Bazaar history.** Every item and its price history, with alerts when something looks unusual.
- **Hypixel status.** A banner shows when SkyBlock is down and when there's news about updates.
- **Accurate metrics and charts.** The database is snapshotted every 2 hours, and the realtime view polls every 30 seconds.

## How it fits together

```
 Minecraft (mod) ──┐
                   ├──►  api.skystats.cc  ──►  Postgres  ◄──  worker (Hypixel + bazaar ingestion)
 skystats.cc (web) ┘          ▲
                              │
 Discord (bot) ───────────────┘
```

You sign in with your Minecraft account. The website shows a pairing code, you run `/skystats link CODE` in game and click **[Confirm]**, and you're in. The mod proves you own the account through Mojang's session server, so your Minecraft access token only ever goes to Mojang.

## Repositories

| Repo | What it is | Stack |
|---|---|---|
| [`server`](https://github.com/skystats-cc/server) | API + background worker + migrations (one image, three processes) | Fastify, Postgres, pg-boss |
| [`web`](https://github.com/skystats-cc/web) | The skystats.cc website | Vite, React, Caddy |
| [`mod`](https://github.com/skystats-cc/mod) | Fabric client mod (multi-version: 26.2, 26.3) | Kotlin, Stonecutter |
| [`discord-bot`](https://github.com/skystats-cc/discord-bot) | Slash commands for Discord | discord.js |
| [`api-spec`](https://github.com/skystats-cc/api-spec) | OpenAPI contract and the generated `@skystats/api-client` | OpenAPI, TypeScript |
| [`infra`](https://github.com/skystats-cc/infra) | Production Compose, Cloudflare Tunnel, backups, deploy scripts, roadmap | Docker, Shell |
