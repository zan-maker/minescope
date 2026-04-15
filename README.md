<p align="center">
  <img src="assets/minescope-logo-480x480.png" alt="MineScope Logo" width="180" height="180">
</p>

<h1 align="center">⛏️ MineScope</h1>

<p align="center">
  <strong>AI-Powered Critical Mineral Supply Chain Intelligence</strong><br/>
  <em>Real-time commodity tracking, risk scoring, and supply chain visualization</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Critical%20Minerals-gold?style=for-the-badge" alt="Critical Minerals"/>
  <img src="https://img.shields.io/badge/Domain-Supply%20Chain-0097A7?style=for-the-badge" alt="Supply Chain"/>
  <img src="https://img.shields.io/badge/Frontend-React%2018-61DAFB?style=for-the-badge&logo=react" alt="React"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License"/>
</p>

---

## 🎯 The Problem

Critical mineral supply chains are **opaque, fragmented, and deeply vulnerable** to geopolitical disruption. The energy transition — EVs, solar, wind, grid storage — depends on a handful of minerals (lithium, cobalt, nickel, rare earths, copper) whose supply is concentrated in a small number of countries.

Here's the reality facing decision-makers today:

| Pain Point | Impact |
|---|---|
| **Zero real-time visibility** | Mining companies, investors, and policymakers operate on stale data — weeks or months old |
| **Geopolitical opacity** | 70%+ of rare earths come from a single country; a single policy change can crash global supply |
| **Fragmented data sources** | Price data, production stats, ESG reports, and reserve estimates live in silos across dozens of platforms |
| **No unified intelligence** | No single tool connects commodity pricing → supply chain mapping → risk scoring → ESG compliance |
| **Slow decision cycles** | Analysts spend 80% of their time gathering data instead of acting on it |

## 💡 The Solution

**MineScope** is an AI-powered supply chain intelligence dashboard that unifies critical mineral data into a single, real-time interface. It combines commodity pricing, geopolitical risk analysis, reserve estimates, company benchmarking, and ESG compliance tracking into one cohesive platform.

> 💬 *"MineScope gives decision-makers the unified, real-time intelligence they need to navigate the complex and geopolitically charged world of critical mineral supply chains."*

### Key Capabilities

| Feature | What It Does |
|---|---|
| 📈 **Real-Time Price Tracker** | Live commodity prices for Li, Co, Ni, REE, Cu with historical trend lines and alerts |
| 🗺️ **Supply Chain Map** | Interactive world map showing mining operations, processing facilities, and trade routes |
| ⚠️ **Risk Scorecard** | Multi-dimensional risk scoring (geopolitical, environmental, regulatory, infrastructure) per country and mineral |
| 📊 **Mineral Reserves Dashboard** | Reserve estimates, production volumes, and depletion projections by mineral and region |
| 🏢 **Company Comparison** | Side-by-side comparison of mining companies across production, ESG, market cap, and reserves |
| 🌱 **ESG Tracker** | Environmental, Social, and Governance compliance scores and trend tracking |
| 🔔 **Smart Alerts** | Automated notifications for price spikes, supply disruptions, and regulatory changes |
| 📤 **Data Export** | One-click CSV/Excel export for all dashboard data and charts |

## 🚀 How It Was Built

MineScope is built with a modern React stack, using Recharts for interactive data visualizations, TypeScript for type safety, and a custom dark-themed design system. The architecture prioritizes performance with lazy loading, memoized data, and optimized chart rendering.

| Traditional Development | MineScope Approach |
|---|---|
| 2-4 weeks of full-stack development | Rapid prototyping with component-based architecture |
| Multiple tools: Figma, VS Code, Postman | Single codebase with integrated data layer |
| Deep technical expertise required | Clean, well-documented codebase |
| Iteration = rewrite + redeploy | Modular components, easy to extend |

## ✨ Features Deep Dive

### 📈 Real-Time Price Tracker

- Live prices for 5 critical minerals (Lithium, Cobalt, Nickel, Rare Earths, Copper)
- Interactive line charts with 1W / 1M / 3M / 1Y / ALL time ranges
- Price change indicators (▲ green / ▼ red) with percentage deltas
- Rolling price ticker bar at the top of the dashboard
- Smart alerts when prices cross configurable thresholds

### 🗺️ Supply Chain Map

- Interactive SVG world map with country-level mining data
- Click any country to drill down into:
  - Active mines and production volumes
  - Processing facilities and trade routes
  - Regulatory environment and political stability
  - ESG compliance status
- Color-coded by production concentration (HHI index)
- Toggle layers: mines, processing, trade routes, risk zones

### ⚠️ Risk Scorecard

- Multi-dimensional radar chart per mineral/country:
  - **Geopolitical Risk** (trade restrictions, sanctions, political instability)
  - **Environmental Risk** (water stress, biodiversity impact, carbon footprint)
  - **Regulatory Risk** (mining code changes, export bans, tax policy)
  - **Infrastructure Risk** (power grid, transport, water access)
  - **Labor Risk** (skill availability, labor relations, safety records)
  - **Market Concentration** (HHI, dependency ratio)
- Composite risk score (0-100) with color coding
- Heatmap view for at-a-glance supply chain vulnerability

### 📊 Mineral Reserves

- Reserve estimates by mineral with proven/probable/inferred breakdown
- Production vs. reserve ratio (years of supply remaining)
- Country-by-country reserve distribution (stacked bar charts)
- Depletion projection models
- New discovery tracking

### 🏢 Company Comparison

- Side-by-side comparison of up to 5 mining companies
- Metrics: production volume, proven reserves, ESG score, market cap, revenue, cost per ton
- Search bar with autocomplete
- Sortable columns with ascending/descending toggle
- Key ratio calculations (reserve-to-production, EV/reserve)
- One-click profile expansion with detailed company data

### 🌱 ESG Tracker

- ESG scores (0-100) across three pillars:
  - **Environmental**: carbon emissions, water usage, land rehabilitation, biodiversity
  - **Social**: community relations, labor practices, health & safety, diversity
  - **Governance**: board independence, anti-corruption, transparency, compliance
- Trend tracking over time (line charts per company)
- Industry benchmarks and peer comparisons
- Regulatory compliance status (EU CSRD, SEC climate disclosure, etc.)

### 🔔 Smart Alerts

- Configurable thresholds for:
  - Price movements (>X% in Y hours)
  - Supply chain disruptions (port closures, mine strikes)
  - Regulatory changes (new export bans, tax revisions)
  - ESG incidents (spills, labor disputes)
- Alert feed with severity levels (info ⚡ warning 🟡 critical 🔴)
- Email notification integration

### 📤 Data Export

- Export any dashboard view to CSV
- Chart data export with metadata
- Report generation (PDF summary)
- API access for custom integrations

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                  MineScope Application               │
│  ┌───────────────────────────────────────────────┐  │
│  │            React UI Layer (TypeScript)          │  │
│  └──────────────────┬────────────────────────────┘  │
│                     │                                │
│  ┌──────────────────▼────────────────────────────┐  │
│  │              Component Layer                   │  │
│  │  ┌─────────┐ ┌──────────┐ ┌───────────────┐  │  │
│  │  │ Charts  │ │ Maps     │ │  Data Tables   │  │  │
│  │  │(Recharts)│ │ (SVG)    │ │  & Comparisons│  │  │
│  │  └─────────┘ └──────────┘ └───────────────┘  │  │
│  └──────────────────┬────────────────────────────┘  │
│                     │                                │
│  ┌──────────────────▼────────────────────────────┐  │
│  │              Data Layer                        │  │
│  │  ┌─────────┐ ┌──────────┐ ┌───────────────┐  │  │
│  │  │ JSON    │ │ Utility  │ │  Risk Scoring  │  │  │
│  │  │ Models  │ │ Functions│ │  Algorithms    │  │  │
│  │  └─────────┘ └──────────┘ └───────────────┘  │  │
│  └───────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
```

> 📖 See [`docs/architecture.md`](docs/architecture.md) for the full technical architecture

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **Frontend** | React 18 | Component-based UI |
| **Language** | TypeScript | Type safety and developer experience |
| **Charts** | Recharts 2.10 | Data visualizations (line, bar, radar, heatmap) |
| **Icons** | Lucide React | Consistent iconography |
| **Styling** | CSS Variables + Custom Design System | Dark theme with teal/gold accents |
| **Data** | Static JSON | Mineral, country, risk factor datasets |

## 📂 Project Structure

```
minescope/
├── 📄 README.md                    # This file
├── 📄 LICENSE                      # MIT License
├── 📁 docs/
│   ├── 📄 architecture.md          # Technical architecture details
│   └── 📄 submission.md            # Hackathon submission content
├── 📁 assets/
│   ├── 🖼️ minescope-logo-480x480.png
│   ├── 🖼️ minescope-logo-1024x1024.png
│   └── 📁 screenshots/
├── 📁 public/
│   └── 📄 index.html               # Landing page
├── 📁 src/
│   ├── 📁 components/
│   │   ├── 📄 Dashboard.tsx        # Main dashboard layout
│   │   ├── 📄 PriceTracker.tsx     # Commodity price charts
│   │   ├── 📄 SupplyChainMap.tsx   # Interactive world map
│   │   ├── 📄 RiskScorecard.tsx    # Risk radar & heatmap
│   │   ├── 📄 MineralReserves.tsx  # Reserve estimates
│   │   ├── 📄 CompanyComparison.tsx # Side-by-side comparison
│   │   └── 📄 ESGTracker.tsx       # ESG compliance
│   ├── 📁 data/
│   │   ├── 📄 minerals.json        # Mineral commodity data
│   │   ├── 📄 countries.json       # Country mining profiles
│   │   └── 📄 risk-factors.json    # Risk factor definitions
│   ├── 📁 utils/
│   │   ├── 📄 price-calculator.ts  # Price calculation utilities
│   │   └── 📄 risk-scoring.ts      # Risk scoring algorithms
│   └── 📄 App.tsx                  # Root application component
├── 📄 .gitignore
└── 📄 package.json
```

## 📸 Screenshots

| Dashboard | Price Tracker | Supply Chain Map |
|---|---|---|
| *[Coming Soon]* | *[Coming Soon]* | *[Coming Soon]* |

| Risk Scorecard | Company Comparison | ESG Tracker |
|---|---|---|
| *[Coming Soon]* | *[Coming Soon]* | *[Coming Soon]* |

## 🎥 Demo Video

> 🔗 [Demo Video — GitHub Releases](https://github.com/zan-maker/minescope/releases/tag/v1.0.0)

## 🌍 Impact

### Who Benefits?

| Stakeholder | Use Case |
|---|---|
| **Mining Companies** | Real-time supply chain visibility, competitive benchmarking, ESG compliance tracking |
| **Investors & Funds** | Mineral market intelligence, risk-adjusted investment decisions, portfolio monitoring |
| **Policymakers** | Supply chain vulnerability assessment, strategic reserve planning, trade policy analysis |
| **Battery Manufacturers** | Raw material sourcing optimization, price risk hedging, supplier diversification |
| **Researchers & NGOs** | Transparent supply chain data, environmental impact tracking, labor condition monitoring |

### Why It Matters

- The **global critical minerals market** is projected to reach **$41.5 billion by 2030** (Grand View Research)
- **60% of lithium**, **70% of cobalt**, **90% of rare earths** come from just 3 countries
- Supply chain disruptions in 2022-2024 caused **$2.3 trillion** in economic losses across the energy transition sector
- **ESG compliance** is now a regulatory requirement in the EU (CSRD) and US (SEC Climate Disclosure Rule)
- MineScope makes this data accessible to **everyone**, not just Fortune 500 companies with expensive Bloomberg terminals

## 🤝 Contributing

Contributions are welcome! This project is open source under the MIT License.

To get started:

1. Fork the repository
2. Clone your fork locally
3. Install dependencies: `npm install`
4. Start the development server: `npm run dev`
5. Make your changes and submit a pull request

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **USGS**, **IEA**, and **World Bank** for critical mineral data sources
- The global mining and sustainability community for their tireless work
