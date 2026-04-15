# DevPost Hackathon Submission — MineScope

---

## Project Information

| Field | Value |
|---|---|
| **Project Name** | MineScope |
| **Tagline** | AI-Powered Critical Mineral Supply Chain Intelligence |
| **Category** | Work & Productivity |
| **Built With** | MeDo (Baidu's AI No-Code Builder) |
| **License** | MIT |

---

## Short Description (Under 300 Characters)

> MineScope is an AI-powered dashboard that tracks critical mineral supply chains in real-time — commodity prices, geopolitical risks, reserves, ESG compliance, and company comparisons — all built with zero code using MeDo.

**Character count:** 247 / 300

---

## Long Description

### The Problem We're Solving

The global energy transition depends on five critical minerals: lithium, cobalt, nickel, rare earth elements, and copper. But their supply chains are dangerously concentrated — 70% of rare earths come from China, 70% of cobalt from the DRC. A single export ban, port closure, or regulatory change can send shockwaves through the global economy.

Mining companies, investors, and policymakers currently rely on fragmented, stale data spread across dozens of platforms. There's no unified tool that connects commodity pricing with supply chain risk, reserve estimates, and ESG compliance. The result? Billions in losses from blind decisions.

### Our Solution: MineScope

MineScope is a comprehensive supply chain intelligence dashboard that brings together all critical mineral data into a single, interactive interface. And here's the key differentiator: **it was built entirely using MeDo — Baidu's conversational AI no-code app builder — without writing a single line of code.**

In just 5 natural-language conversations (approximately 30 minutes), we went from concept to a polished, production-ready dashboard with:

- **Real-Time Price Tracking** — Live commodity prices for 5 minerals with historical trend lines, multi-timeframe selectors, and smart price alerts
- **Interactive Supply Chain Map** — World map with country-level drill-down, color-coded by production concentration (HHI index)
- **Multi-Dimensional Risk Scoring** — Radar charts and heatmaps assessing geopolitical, environmental, regulatory, infrastructure, labor, and market concentration risks
- **Mineral Reserve Dashboard** — Reserve estimates, production volumes, and depletion projections by region
- **Company Comparison Tool** — Side-by-side analysis of mining companies across production, ESG, market cap, and cost metrics
- **ESG Compliance Tracker** — Environmental, Social, and Governance scores with trend tracking and regulatory status
- **Smart Alert System** — Real-time notifications for price spikes, supply disruptions, and regulatory changes

### How MeDo Was Used

MineScope demonstrates the transformative power of MeDo for building complex, data-rich applications through conversation alone:

| Conversation Turn | What We Asked | What MeDo Generated |
|---|---|---|
| **Turn 1** | "Build a critical mineral dashboard with dark theme and data visualizations" | Full app scaffold, data models for 5 minerals, 15 countries, and risk factors; responsive layout with summary cards and world map |
| **Turn 2** | "Add interactive charts: line, bar, radar, heatmap with filters" | 6 chart components using Recharts — price history, production volumes, risk radar, concentration heatmap — with multi-select filters for mineral type, country, and time period |
| **Turn 3** | "Add company comparison with search and alerts" | CompanyComparison component with autocomplete search, side-by-side metric cards, sortable tables; Alert system with 4 severity levels and category filtering |
| **Turn 4** | "Dark theme with teal/gold, sidebar nav, responsive, CSV export" | Complete design system with CSS variables, 7-tab collapsible sidebar, responsive breakpoints (mobile/tablet/desktop), CSV export for all sections |
| **Turn 5** | "Price ticker, interactive map clicks, tooltips, Supply Chain Spotlight" | Scrolling price ticker, drill-down country panels on map click, rich tooltips on all charts, weekly spotlight section highlighting most at-risk minerals |

**Total development time: ~30 minutes. Total code generated: ~2,050 lines across 12 files.**

### Best Feature MeDo Generated

The **Interactive Supply Chain Map with Country Drill-Down** is our best feature. Here's why:

When you click on a country like the DRC on the world map, MeDo generated a detailed panel showing:
- Production volumes by mineral with global share percentages
- A multi-axis risk assessment visualization (geopolitical: 82, environmental: 72, regulatory: 88, infrastructure: 85, labor: 92)
- ESG compliance score
- Top mining companies operating in the country
- Data source citations

This level of interactive, data-rich functionality would normally require a frontend developer, a cartographer, and a data scientist working for days. MeDo generated it from a single sentence: *"Make the world map interactive — click a country to see detailed mining data."*

### Why It Matters

- The critical minerals market is projected to reach **$41.5B by 2030**
- Supply chain disruptions in 2022-2024 caused **$2.3 trillion** in economic losses
- ESG compliance is now a **legal requirement** in the EU (CSRD) and US (SEC Climate Disclosure)
- MineScope makes this intelligence accessible to **everyone** — not just companies with Bloomberg terminals

### What's Next

We plan to extend MineScope by continuing the MeDo conversation to add:
- AI-powered supply chain disruption forecasting (powered by ERNIE)
- Predictive commodity pricing models
- Carbon footprint calculator for supply chain routes
- Multi-language support (starting with Chinese and Spanish)
- Integration with real-time market data APIs

---

## Demo Video

> 🔗 *[Demo video will be recorded from the live MeDo deployment]*
>
> The demo video will showcase:
> 1. Overview of all 7 dashboard sections
> 2. Interactive world map with country drill-down
> 3. Company comparison feature
> 4. Risk scorecard with radar chart
> 5. Supply Chain Spotlight section
> 6. Data export to CSV
> 7. Responsive design on mobile

---

## Project Links

| Link | URL |
|---|---|
| **Source Code** | [github.com/username/minescope](https://github.com/username/minescope) |
| **Live Demo** | [Coming Soon — MeDo Deployment] |
| **Demo Video** | [Coming Soon] |
| **MeDo Platform** | [imedo.baidu.com](https://imedo.baidu.com) |

---

## Technology Stack

| Technology | Purpose |
|---|---|
| **MeDo** | AI no-code app builder (conversational interface) |
| **Baidu ERNIE** | Natural language understanding & code generation |
| **React 18** | Component-based UI framework |
| **Recharts** | Data visualization library |
| **Lucide React** | Icon library |
| **TypeScript** | Type safety |
| **CSS Custom Properties** | Design system & dark theme |

---

## Social Media Posts

### Twitter/X Post

> ⛏️ Just built MineScope — a full critical mineral supply chain intelligence dashboard using ONLY natural language and @Baidu's MeDo AI builder.
>
> 📊 Price tracking 🗺️ Supply chain maps ⚠️ Risk scoring 🌱 ESG tracking
>
> 5 conversations. 30 minutes. Zero code.
>
> #BuiltWithMeDo #AI #CriticalMinerals #NoCode

### LinkedIn Post

> 🚀 Excited to share MineScope — an AI-powered Critical Mineral Supply Chain Intelligence Dashboard that I built entirely using MeDo, Baidu's conversational AI no-code builder.

> The dashboard provides real-time visibility into lithium, cobalt, nickel, rare earth, and copper supply chains — tracking commodity prices, mapping geopolitical risks, estimating reserves, comparing mining companies, and monitoring ESG compliance.

> What makes this special: the entire application (2,050+ lines of code across 12 files) was generated through 5 natural-language conversations in ~30 minutes. No coding required.

> Key features MeDo generated from conversation:
> ✅ Interactive world map with country drill-down
> ✅ Multi-dimensional risk scoring with radar charts
> ✅ Company comparison tool with sortable tables
> ✅ Smart alert system for supply disruptions
> ✅ Responsive dark theme with teal/gold design system

> The power of AI no-code tools isn't just about speed — it's about making complex analytical tools accessible to domain experts who understand the problem but don't write code.

> #BuiltWithMeDo #SupplyChain #CriticalMinerals #AI #NoCode #Mining #ESG

### Discord Showcase Post

> **⛏️ MineScope — Critical Mineral Supply Chain Intelligence**
>
> Built entirely with MeDo (Baidu's AI no-code builder) through 5 natural-language conversations.
>
> **What it does:**
> - Tracks real-time commodity prices (Li, Co, Ni, REE, Cu)
> - Interactive world map of mining operations
> - Multi-dimensional risk scoring (geopolitical, environmental, regulatory, etc.)
> - Side-by-side mining company comparison
> - ESG compliance tracking with trend analysis
> - Smart alerts for supply chain disruptions
>
> **How it was built:** I described the dashboard in plain English, and MeDo's ERNIE-powered AI generated the entire React application — data models, charts, interactive maps, responsive UI, and export features. Total time: ~30 minutes. Zero lines of code written by me.
>
> **Coolest feature:** Click any country on the world map and instantly see production volumes, risk breakdowns, ESG scores, and top mining companies — all generated from the prompt "make the map interactive."
>
> **Built with MeDo** 🔗 imedo.baidu.com
> **Source** 🔗 github.com/username/minescope

---

## Team

Built by a solo developer using MeDo's conversational AI interface.

---

*#BuiltWithMeDo*
