# MineScope — Technical Architecture

> This document describes the technical architecture of the MineScope critical mineral supply chain intelligence dashboard.

---

## System Overview

MineScope is a client-side React application that provides critical mineral supply chain intelligence through interactive data visualizations. Built with TypeScript for type safety and Recharts for rich charting, the application delivers a comprehensive view of global mineral markets through an intuitive dark-themed interface.

```
┌─────────────────────────────────────────────────────────────┐
│                  MineScope Application                       │
│                                                              │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              React UI Layer (TypeScript)              │    │
│  │                                                      │    │
│  │  Component Assembly → State Management → Rendering   │    │
│  └──────────────────────┬──────────────────────────────┘    │
│                          │                                   │
│  ┌──────────────────────▼──────────────────────────────┐    │
│  │              MineScope Components                    │    │
│  │                                                      │    │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────────────┐  │    │
│  │  │ UI Layer │  │ Chart    │  │ Data Layer       │  │    │
│  │  │ (React)  │  │ Layer    │  │ (JSON + Utils)   │  │    │
│  │  └──────────┘  │(Recharts)│  └──────────────────┘  │    │
│  │                  └──────────┘                         │    │
│  └─────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘
```

---

## Component Architecture

```
App.tsx
├── PriceTicker (fixed top bar)
│   └── TickerItem × N (scrolling mineral prices)
├── Sidebar (collapsible navigation)
│   ├── NavItem: Dashboard
│   ├── NavItem: Price Tracker
│   ├── NavItem: Supply Chain Map
│   ├── NavItem: Risk Analysis
│   ├── NavItem: Reserves
│   ├── NavItem: Company Compare
│   └── NavItem: ESG
├── Main Content Area (route-based)
│   ├── Dashboard
│   │   ├── KpiCards (5 summary metrics)
│   │   ├── PriceOverview (mini chart)
│   │   ├── RiskSummary (top risks)
│   │   ├── SupplyChainSpotlight (weekly highlights)
│   │   └── AlertFeed (recent alerts)
│   ├── PriceTracker
│   │   ├── TimeRangeSelector
│   │   ├── MineralFilter
│   │   ├── PriceLineChart (Recharts)
│   │   └── PriceTable (sortable)
│   ├── SupplyChainMap
│   │   ├── MineralFilter
│   │   ├── LayerToggle (mines, routes, risk)
│   │   ├── WorldMap (SVG, interactive)
│   │   └── CountryDetailPanel (drill-down)
│   ├── RiskScorecard
│   │   ├── MineralSelector
│   │   ├── RadarChart (6-axis)
│   │   ├── RiskHeatmap (mineral × country)
│   │   └── RiskBreakdownTable
│   ├── MineralReserves
│   │   ├── ReserveBarChart
│   │   ├── CountryDistributionChart
│   │   ├── DepletionProjection
│   │   └── ReserveDataTable
│   ├── CompanyComparison
│   │   ├── SearchBar (autocomplete)
│   │   ├── CompanyCard × N
│   │   ├── ComparisonTable (sortable)
│   │   ├── ComparisonRadarChart
│   │   └── MetricCards
│   └── ESGTracker
│       ├── CompanySelector
│       ├── ESGScoreCards (E, S, G)
│       ├── ESGTrendChart
│       ├── RegulatoryStatus
│       └── PeerBenchmark
└── Footer
    ├── Data Source Citations
    └── Export Controls
```

---

## Data Architecture

### Data Flow

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ JSON Data    │────▶│ Utility      │────▶│ React        │
│ Files        │     │ Functions    │     │ Components   │
│              │     │              │     │              │
│ minerals.json│     │ price-calc   │     │ Charts       │
│ countries.json│    │ risk-scoring │     │ Maps         │
│ risk-factors │     │ export-csv   │     │ Tables       │
└──────────────┘     └──────────────┘     └──────────────┘
```

### Data Models

#### Mineral (`src/data/minerals.json`)

```typescript
interface Mineral {
  id: string;              // Unique identifier (e.g., "lithium")
  name: string;            // Full name
  symbol: string;          // Chemical symbol
  price: number;           // Current price in USD/ton
  unit: string;            // Price unit
  change: number;          // % change from previous period
  production: string;      // Annual production volume
  topProducer: string;     // Country with highest production
  reserve: string;         // Global proven reserves
  category: string;        // End-use category
  riskScore: number;       // Composite supply chain risk (0-100)
}
```

#### Country (`src/data/countries.json`)

```typescript
interface Country {
  name: string;            // Full country name
  code: string;            // ISO 3166-1 alpha-2
  region: string;          // Geographic region
  minerals: string[];      // Active mineral production
  productionVolume: Record<string, number>; // mineral → tons/year
  politicalStability: number;  // 0-100 (World Bank Governance)
  regulatoryEnvironment: number; // 0-100 (ease of mining)
  esgScore: number;        // Composite ESG (0-100)
  topCompanies: string[];  // Major mining companies
  riskFactors: {
    geopolitical: number;
    environmental: number;
    regulatory: number;
    infrastructure: number;
    labor: number;
  };
}
```

#### Risk Factors (`src/data/risk-factors.json`)

```typescript
interface RiskFactorCategory {
  id: string;
  name: string;
  description: string;
  weight: number;          // Weight in composite score (0-1)
  indicators: string[];    // Sub-indicators
}

interface RiskFactorsData {
  categories: RiskFactorCategory[];
}
```

---

## Design System

### Color Tokens

```css
:root {
  /* Background layers */
  --bg-base: #050a15;
  --bg-surface: #0d1520;
  --bg-elevated: #142030;
  --bg-hover: #1a2940;

  /* Text hierarchy */
  --text-primary: #f1f5f9;
  --text-secondary: #94a3b8;
  --text-muted: #64748b;

  /* Primary accent — Teal */
  --teal-50: #f0fdfa;
  --teal-100: #ccfbf1;
  --teal-400: #2dd4bf;
  --teal-500: #14b8a6;
  --teal-600: #0d9488;
  --teal-700: #0f766e;

  /* Secondary accent — Gold */
  --gold-300: #fbbf24;
  --gold-400: #f59e0b;
  --gold-500: #d4a017;
  --gold-600: #b8860b;

  /* Semantic */
  --success: #22c55e;
  --warning: #eab308;
  --danger: #ef4444;
  --info: #3b82f6;

  /* Borders */
  --border-default: #1e293b;
  --border-subtle: #0f172a;
}
```

### Typography

| Level | Size | Weight | Line Height | Color |
|---|---|---|---|---|
| H1 | 24px | 700 | 1.3 | `--text-primary` |
| H2 | 20px | 600 | 1.35 | `--text-primary` |
| H3 | 16px | 600 | 1.4 | `--text-primary` |
| Body | 14px | 400 | 1.5 | `--text-secondary` |
| Caption | 12px | 400 | 1.4 | `--text-muted` |
| Data/Mono | 14px | 500 | 1.5 | `--teal-400` |

### Spacing Scale

4px base unit: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96

### Component States

| State | Background | Border | Shadow |
|---|---|---|---|
| Default | `--bg-surface` | `--border-default` | none |
| Hover | `--bg-hover` | `--border-default` | 0 2px 8px rgba(0,0,0,0.3) |
| Active | `--bg-elevated` | `--teal-600` | 0 0 0 1px `--teal-600` |
| Disabled | `--bg-base` | `--border-subtle` | none |

### Responsive Breakpoints

| Breakpoint | Width | Sidebar | Grid Columns | Card Layout |
|---|---|---|---|---|
| Mobile | < 768px | Bottom nav | 1 | Stack |
| Tablet | 768-1024px | Icon sidebar | 2 | 2 per row |
| Desktop | > 1024px | Full sidebar | 3 | 5 per row |

---

## Chart Library Configuration

### Recharts Theme

```typescript
const chartTheme = {
  colors: {
    lithium: '#14b8a6',    // Teal
    cobalt: '#8b5cf6',     // Purple
    nickel: '#f59e0b',     // Gold
    rareEarths: '#ef4444', // Red
    copper: '#f97316',     // Orange
  },
  grid: {
    stroke: '#1e293b',
    strokeWidth: 1,
  },
  axis: {
    tick: { fill: '#64748b', fontSize: 12 },
    axisLine: { stroke: '#1e293b' },
  },
  tooltip: {
    backgroundColor: '#142030',
    border: '1px solid #1e293b',
    borderRadius: 8,
    contentStyle: { color: '#f1f5f9' },
  },
  legend: {
    wrapperStyle: { color: '#94a3b8' },
  },
};
```

### Chart Types Used

| Chart | Component | Library | Use Case |
|---|---|---|---|
| Line Chart | `PriceLineChart` | Recharts `LineChart` | Historical commodity prices |
| Bar Chart (Horizontal) | `ProductionBarChart` | Recharts `BarChart` | Country production volumes |
| Bar Chart (Vertical) | `ReserveBarChart` | Recharts `BarChart` | Mineral reserve distribution |
| Radar Chart | `RiskRadarChart` | Recharts `RadarChart` | Multi-factor risk assessment |
| Heatmap | `ConcentrationHeatmap` | Custom SVG | Supply chain concentration |
| Stacked Area | `DepletionChart` | Recharts `AreaChart` | Reserve depletion projection |
| Composed | `ComparisonChart` | Recharts `ComposedChart` | Company metric comparison |

---

## Interaction Patterns

### Navigation

- **Sidebar**: Persistent left navigation with icon + label
- **Collapsible**: Toggle to icon-only mode on desktop
- **Mobile**: Converts to bottom tab bar on < 768px
- **Active state**: Teal left border + subtle background highlight
- **Keyboard navigation**: Arrow keys to move, Enter to select

### Map Interactions

- **Hover**: Country highlight + tooltip (name, top mineral, volume)
- **Click**: Drill-down panel slides in from right
- **Filter**: Dropdown to filter by mineral type
- **Layers**: Toggle buttons for mines, trade routes, risk overlay
- **Back**: Close drill-down panel, return to map view

### Chart Interactions

- **Tooltip**: Rich tooltip on hover (value, comparison, context)
- **Legend toggle**: Click legend items to show/hide series
- **Time range**: Button group to switch between 1W / 1M / 3M / 1Y / ALL
- **Filter**: Multi-select dropdowns for mineral type and country
- **Export**: CSV export button in chart header

### Table Interactions

- **Sort**: Click column header to sort asc/desc
- **Sort indicator**: Arrow icon showing current sort direction
- **Search**: Debounced text search with autocomplete
- **Selection**: Checkbox for multi-select operations
- **Pagination**: 25/50/100 rows per page

### Alert Interactions

- **Severity filter**: Quick filter buttons (All, Info, Warning, High, Critical)
- **Category filter**: Dropdown (price, supply, regulatory, esg, geopolitical)
- **Dismiss**: Individual alert dismissal
- **Mark all read**: Bulk action
- **Auto-scroll**: New alerts auto-scroll into view

---

## Performance Considerations

- **Lazy loading**: Tab-based route splitting — only active tab's components are rendered
- **Chart optimization**: Recharts `isAnimationActive` set to `false` for datasets > 500 points
- **Map optimization**: SVG world map uses simplified paths (~50KB total)
- **Data pagination**: Tables use virtual scrolling for > 100 rows
- **Debounced inputs**: Search and filter inputs debounced at 300ms

### Data Refresh Strategy

- Static JSON data loaded at app initialization
- Simulated "real-time" updates via setInterval (60s for prices)
- Chart data memoized to prevent unnecessary re-renders

---

## Export Format

### CSV Export Schema

```
minescope_{section}_{YYYY-MM-DD}.csv

Headers:
- Export_Date: ISO 8601 timestamp
- Section: dashboard/prices/risk/reserves/companies/esg
- Filters_Applied: JSON string of active filters
- Data_Source: Primary data source attribution
- [Section-specific columns...]
```
