# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Singapore-based CS2 players who participate in Hack vs Hack (HvH) game modes on community servers. They check the tracker during gaming sessions to see which servers are live, who's playing, and to join quickly via Steam. The audience is a niche but active subculture within the broader CS2 community.

## Product Purpose

Real-time visibility into the Singapore HvH server landscape: which servers are online, how many players are connected, what maps are running, and whether the server version is current. One-click join via Steam protocol. Eliminates the friction of manually checking servers or relying on stale server lists.

## Positioning

A purpose-built, zero-dependency, instant-loading server browser for a specific niche — Singapore HvH — that generic server browsers and the upstream API alone do not serve well. The combination of direct A2S live queries, real-time SSE streaming, and Steam connect integration in an ultra-lightweight package is the meaningful differentiator.

## Operating Context

Used during active gaming sessions — the visitor is at their computer, deciding which server to join. Speed and scannability matter. The tracker runs alongside the game or in a second monitor. Players also monitor who's online to find regulars or avoid certain opponents.

## Capabilities and Constraints

- Zero npm dependencies — pure Node.js server with vanilla HTML/CSS/JS frontend
- Real-time A2S (Source Engine UDP) protocol queries to each Singapore server
- Server-Sent Events (SSE) for live streaming updates (~8 second intervals)
- Steam protocol connect (`steam://connect/`) and clipboard IP copy
- Player name and session duration tracking
- CS2 version comparison to flag outdated servers
- Visitor presence tracking (in-memory, TTL-based, no persistence)
- All state is in-memory — no database, no authentication, no persistence
- External data source: `https://hvh.wtf/api/servers`

## Brand Commitments

- **Killua identity:** The Killua (Hunter x Hunter) reference is preserved through the product name and community context, though the visual aesthetic has evolved from the original dark anime-inspired direction.
- **Liquid Glass aesthetic:** White ground, translucent glass-morphism panels with caustic shimmer, water/fluid ripple interactions, and liquid fill animations. The established visual world is light, clean, and water-themed.
- **Color language:** Soft blue (`--water-deep: #4aa8e0`) as the primary accent, with green/red status indicators. White glass panels on a pale blue ground (`--bg: #f5f9fd`).
- **Typography:** Inter (weights 400–800) with aggressive weight/size contrast for hierarchy. Monospace for server addresses.
- **Name:** "CS2 HVH" as the hero brand on the interface.

## Evidence on Hand

- Live production site running and serving real Singapore HvH server data
- SVG assets: `flag-sg.svg` (Singapore flag icon), `killua-inspired-bg.svg` (brand background), `mirage-map.svg`, `mirage-map.jpg`, `jdm-bg.svg`
- Google Fonts: Inter (weights 400-800)
- Complete working backend (`server.js`) and frontend (`public/index.html`)

## Product Principles

1. **Speed first.** The tracker must load instantly and update without friction — players are mid-session and every second of latency loses them to a competing tab.
2. **Zero overhead.** No build step, no dependencies, no infrastructure bloat. The simplicity is the product.
3. **Community tool, not a platform.** This serves a niche; it should feel like it was built by one of them, not shipped by a company.
4. **Live data is the interface.** Real server and player information is the core value — everything else is chrome that must earn its space.
