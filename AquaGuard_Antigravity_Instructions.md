# Antigravity IDE Build Instructions

## AI-Based Intelligent Water Pipeline Health Monitoring and Failure Prevention System

## 1. Goal

Build a polished, responsive web dashboard for a BTech AI/ML project
focused on monitoring water-pipeline health in Kerala.

The dashboard must provide one central interface to access the project's
modules. Build the frontend and navigation first, using clearly marked
mock/demo data wherever the backend, datasets, GIS exports, AI models,
or hardware are not yet available.

**Important:** This is a student prototype, not a production
water-utility control system. Do not imply that mock readings are real
KWA data, that model scores are validated probabilities, or that the
application can control real valves.

## 2. Recommended technology stack

Use the following unless the existing repository already uses an
equivalent stack:

-   Frontend: React + TypeScript
-   Build tool: Vite
-   Styling: Tailwind CSS
-   Components/icons: use a consistent accessible component style and
    Lucide icons
-   Charts: Recharts
-   Map: React Leaflet with OpenStreetMap tiles
-   Backend integration later: Python + FastAPI
-   Database integration later: PostgreSQL + PostGIS

Before changing files, inspect the current repository and preserve
working code. If it is empty, scaffold the frontend. Do not create a
second app inside an existing app.

## 3. Product name and visual design

Use the working name **AquaGuard Kerala**.

Subtitle: **Intelligent Water Pipeline Monitoring System**

Design direction: **formal government/public-utility portal**, inspired
by the clear, restrained style of official Indian government and Kerala
government service websites, while remaining modern and usable.

-   Use an official, administrative visual language rather than a flashy
    startup/SaaS look.
-   Use a restrained palette: deep navy or government blue, white, light
    grey, and subtle teal. Use amber for warnings and red for critical
    alerts. Do not rely on colour alone; include text labels and icons.
-   Use a compact government-portal-style top header with the project
    title, a simple emblem-style water/pipeline mark (not an official
    government seal), and clear navigation. If appropriate, include a
    small line such as "Academic Prototype \| Kerala"---do not imply the
    site is an official Kerala Water Authority or government website.
-   Prefer clean rectangular panels, thin borders, modest corner
    rounding, restrained shadows, compact spacing, and information-dense
    tables. Avoid giant rounded cards, gradients, glassmorphism, neon
    colours, oversized typography, animated backgrounds, and decorative
    effects.
-   Use formal, readable typography and clear section headings. Keep
    labels descriptive and terminology consistent with public-utility
    operations.
-   Use formal interface wording, for example "Monitoring Overview",
    "Pipeline Network", "Incident Register", "Maintenance Status", and
    "Reports". Avoid overly casual copy.
-   Show the prototype status visibly: "Academic Prototype --- Demo /
    Simulated Data". Do not use official government logos, seals, or
    branding unless explicitly supplied and authorized. Do not claim
    affiliation, endorsement, or official KWA status.
-   Keep the interface accessible, responsive for desktop/tablet/mobile,
    and easy to navigate, with visible keyboard focus, sufficient
    contrast, and labels for form controls.
-   Include loading, empty, and error states. Keep charts and maps
    practical and subordinate to the information users need.

The interface should resemble a credible government water-utility
monitoring portal---not a generic landing page or flashy commercial
dashboard.

## 4. Main application layout

Create a persistent left sidebar with the following navigation items:

1.  Overview
2.  Pipeline GIS Map
3.  Live Monitoring
4.  Leak & Burst Detection
5.  Failure Risk Assessment
6.  Fault Localization & Impact
7.  Incidents & Maintenance
8.  Data & Models
9.  Reports & Analytics
10. Settings / About (simple placeholder is acceptable)

Each item must navigate to a real page or clearly designed placeholder
page. Do not make buttons that do nothing. Use a shared layout, active
navigation state, page title, and breadcrumbs or compact page context.

Header requirements: - Project name/logo mark. - Current selected area,
initially labelled "Demo Area, Kerala". - Data mode badge: "Simulation
mode". - Notification icon linking to incidents/alerts. - Profile/user
menu may be a simple demo control; do not implement fake authentication.

## 5. Overview page

This is the default landing page. Include:

### Summary cards

-   Monitored pipe segments
-   Active alerts
-   High-risk segments
-   Data/source status

Use believable mock values and clearly mark the whole dashboard as
**Demo / Simulated Data**. Avoid presenting fake values as actual Kerala
or KWA statistics.

### Main content

-   A pipeline map preview or a useful map placeholder.
-   Recent incidents table with incident ID, pipe segment, event type,
    severity, time, and status.
-   Pressure and flow trend chart for a selected monitoring point.
-   High-risk pipe segments list with risk category and recommended
    follow-up.
-   Quick links to detection, map, and incident pages.

### Interactions

-   Clicking an incident opens its detail view or navigates to the
    incident module with that incident selected.
-   Clicking a pipe segment opens its detail panel/page.
-   Clicking summary cards navigates to the relevant filtered module.
-   Add date/time range or area filters where useful. Filters must
    visibly affect displayed demo data.

## 6. Module specifications

### 6.1 Pipeline GIS Map

-   Display a map using React Leaflet and OpenStreetMap.
-   Show clearly fictional/demo pipe segments and junctions until
    authorized real GIS data is available.
-   Use a simple demo network with connected line segments and node
    markers. Do not draw fake lines across real Kerala geography and
    imply they are actual pipes.
-   Provide a legend for normal, warning, high-risk, and incident
    states.
-   Include filters for status, risk, and pipe segment ID.
-   Clicking a segment opens a side panel with segment ID, length,
    diameter, material, connected nodes, current status, and data
    source.
-   If no real GIS geometry exists, offer a "Demo Network" view and an
    obvious "Sample geometry" label.
-   Structure map data so it can later be replaced with KWA-authorized
    GeoJSON/KML or PostGIS data.

### 6.2 Live Monitoring

-   Show pressure and flow readings for selectable demo monitoring
    points.
-   Provide time-series charts, current reading, recent minimum/maximum,
    and status.
-   Include a simulation playback/start-stop control if feasible; it
    must operate on local demo data, not pretend to read hardware.
-   Show the reading timestamp and source ("Simulated").
-   Prepare an adapter/service boundary for future sensor or FastAPI
    integration.

### 6.3 Leak & Burst Detection

-   Provide an interface for selecting a monitoring point or uploading a
    supported sample CSV.
-   Show a detection result: normal / possible leak / possible burst /
    other anomaly.
-   Display supporting pressure/flow trends, alert severity, timestamp,
    model version, and confidence only if the demo model actually
    provides it.
-   If no trained model exists, use a clearly labelled demo/rule-based
    detector. Do not call arbitrary random output an AI prediction.
-   Include a small "How this alert was triggered" explanation.
-   Keep leak detection (present abnormal event) separate from future
    failure-risk prediction.

### 6.4 Failure Risk Assessment

-   Show a sortable/filterable pipe-segment table with pipe attributes,
    available history, risk category, and recommended inspection
    priority.
-   Include a risk-distribution chart and a segment detail view.
-   If no validated historical failure model exists, use "Prototype risk
    score" or "Illustrative demo score", not "probability of failure".
-   Show which fields are missing and explain that reliable future
    failure prediction needs suitable historical pipe-failure labels.
-   Do not fabricate real failure history.

### 6.5 Fault Localization & Impact

-   Show a selected incident and a ranked list of candidate pipe
    segments.
-   Display the evidence used, such as which monitoring points show
    pressure/flow anomalies.
-   Visualize connected nodes and pipes for the demo network.
-   Show potentially affected downstream/connected sections and
    candidate isolation valves only when the graph data supports the
    calculation.
-   Label results "Estimated" or "Demo simulation".
-   Do not claim exact coordinates from a single reading and do not
    issue valve-control commands.

### 6.6 Incidents & Maintenance

-   Create a searchable/filterable incident table with ID, event type,
    segment, severity, detected time, status, and assigned action.
-   Include incident detail with timeline, readings, notes, and status.
-   Allow demo-only status changes such as Open, Investigating,
    Resolved, and Dismissed.
-   Keep an audit-style local activity log if practical.
-   Make clear that changes are stored locally/in demo state until
    backend persistence is added.

### 6.7 Data & Models

-   Show available demo datasets and their source/status.
-   Include CSV upload and preview for supported tabular data, with
    clear validation errors.
-   Include model cards for the leak detector and risk model: purpose,
    input fields, training-data source, version, and validation status.
-   Provide a model evaluation view for precision, recall, F1,
    false-positive rate, and other available metrics.
-   Do not invent model metrics. If models are not trained, show "Not
    evaluated yet".
-   Keep external/public datasets separate from Kerala-specific GIS data
    and synthetic simulation data.

### 6.8 Reports & Analytics

-   Show date-filtered counts of incidents, severity distribution, and
    risk distribution using current demo data.
-   Provide a printable report view and CSV export for tables if
    feasible.
-   Label demo reports clearly.
-   Do not report water saved, money saved, or real operational impact
    unless calculated from valid inputs and assumptions are displayed.

### 6.9 Settings / About

-   Display project description, current data mode, data limitations,
    and software version.
-   Include a simple switch between "Demo data" and "Connected backend"
    only if the latter is genuinely configured. Otherwise show backend
    integration as "Not connected".

## 7. Data model and shared identifiers

Use consistent IDs across all pages so an incident can connect to a pipe
segment, readings, a map feature, and a model output.

Suggested frontend types:

``` ts
type PipeSegment = {
  id: string;
  startNodeId: string;
  endNodeId: string;
  lengthM?: number;
  diameterMm?: number;
  material?: string;
  geometry?: GeoJSON.LineString;
  status: "normal" | "warning" | "high-risk" | "incident" | "unknown";
  dataSource: "demo" | "imported" | "backend";
};

type Reading = {
  id: string;
  monitoringPointId: string;
  pipeSegmentId?: string;
  timestamp: string;
  pressure?: number;
  pressureUnit?: string;
  flowRate?: number;
  flowUnit?: string;
  source: "simulated" | "imported" | "sensor";
};

type Incident = {
  id: string;
  pipeSegmentId: string;
  type: "leak" | "burst" | "pressure-anomaly" | "flow-anomaly" | "sensor-fault" | "unknown";
  severity: "low" | "medium" | "high" | "critical";
  detectedAt: string;
  status: "open" | "investigating" | "resolved" | "dismissed";
  source: "demo" | "model" | "operator";
  explanation?: string;
};

type RiskAssessment = {
  pipeSegmentId: string;
  category: "low" | "medium" | "high" | "unknown";
  score?: number;
  scoreLabel: "prototype score" | "validated probability" | "not evaluated";
  explanation?: string;
};
```

Adapt these types as needed, but keep shared IDs consistent. Do not mix
simulated and imported/real data without displaying their source.

## 8. Architecture and code organization

Keep UI components, pages, types, and data services separate. A possible
structure:

``` text
src/
  app/
    App.tsx
    routes.tsx
  components/
    layout/
      AppShell.tsx
      Sidebar.tsx
      Topbar.tsx
    cards/
    charts/
    tables/
    maps/
    common/
  pages/
    OverviewPage.tsx
    PipelineMapPage.tsx
    MonitoringPage.tsx
    DetectionPage.tsx
    RiskAssessmentPage.tsx
    LocalizationPage.tsx
    IncidentsPage.tsx
    DataModelsPage.tsx
    ReportsPage.tsx
    SettingsPage.tsx
  data/
    demoPipes.ts
    demoReadings.ts
    demoIncidents.ts
  services/
    pipelineService.ts
    monitoringService.ts
    detectionService.ts
    riskService.ts
    incidentService.ts
  types/
    index.ts
```

This is a guide, not a requirement to duplicate folders that already
exist. Use a service layer so demo data can later be replaced by API
calls without rewriting pages.

## 9. Backend integration readiness

The frontend should be usable without a backend. Create typed service
functions and isolate mock data behind those functions.

Potential future FastAPI endpoints: - `GET /api/pipelines` -
`GET /api/pipelines/{id}` -
`GET /api/readings?point_id=...&from=...&to=...` -
`POST /api/detection/predict` - `GET /api/risks` -
`GET /api/incidents` - `PATCH /api/incidents/{id}` -
`GET /api/network/{segment_id}/impact` - `GET /api/models/status`

Do not implement pretend API responses that claim to come from a live
backend. If no backend URL is configured, use the demo service and
display that status clearly.

## 10. Data integrity and safety rules

-   No real KWA data is assumed to be available.
-   Never label demo or synthetic records as real Kerala pipeline data.
-   Do not invent sensor readings, model accuracy, failure
    probabilities, incident counts, or water-loss savings as real
    results.
-   Keep model predictions advisory and explain their evidence and
    limitations.
-   Do not implement actual valve control or any other physical
    infrastructure command.
-   Validate uploaded CSV columns and show actionable errors.
-   Treat personal consumer data as restricted; use synthetic or
    aggregated data for the prototype.
-   Provide sensible empty states when a dataset or model is
    unavailable.

## 11. Development order

Implement in this order:

1.  Inspect the repository and report the current stack.
2.  Build the application shell, sidebar, routing, typography, and
    responsive layout.
3.  Build the Overview page with clearly labelled demo data.
4.  Add shared types and demo data services.
5.  Implement all module pages with realistic interactions and
    appropriate empty states.
6.  Add the demo pipeline map and charts.
7.  Verify that all navigation, filters, table search, row selection,
    and demo status changes work.
8.  Run the app, check the browser console, fix errors, and document how
    to run it.
9.  Summarize created/changed files and list what remains a placeholder.

Do not stop after creating a static mockup. The navigation and key demo
interactions should work. Do not build the hardware integration yet.

## 12. Acceptance checklist

-   [ ] Application starts using documented commands.
-   [ ] All sidebar destinations open the correct page.
-   [ ] Layout works on desktop and tablet.
-   [ ] Overview cards and charts use labelled demo data.
-   [ ] Map clearly distinguishes sample geometry from real GIS data.
-   [ ] Filters and search change the displayed content.
-   [ ] Selecting a pipe or incident opens relevant details.
-   [ ] Incident demo status changes are reflected throughout the UI.
-   [ ] CSV import validates columns and displays understandable errors.
-   [ ] No fake model metrics or fake live readings are presented as
    real.
-   [ ] No dead buttons or broken links.
-   [ ] No real hardware control is implemented.
-   [ ] README includes setup/run commands, architecture, demo-data
    limitations, and next steps.

**First task:** inspect the existing project and implement the dashboard
shell plus Overview page. Then proceed module by module while keeping
the application runnable.
