# Architecture & Folder Structure: projects_realestate

This document provides an overview of the folder organization of the `projects_realestate` Next.js application after its migration to a Domain Driven Design (DDD) structure for improved maintainability, collaboration, and feature scalability.

---

## High-Level Folder Diagram

```mermaid
graph TD
  A["projects_realestate/"]
  A1["assets/"]:::sub
  A2["attachments/"]:::sub
  AA["figmafiles/"]:::sub
  AB["kavia-docs/"]:::sub
  B["README.md"]
  C["next.config.js"]
  D["package.json"]
  E["pages/"]
  F["domains/"]
  G["shared/"]
  H["utils/"]

  F1["property/"]:::sub
  F2["search/"]:::sub
  F1A["ImageScrollbar.jsx"]
  F1B["Property.jsx"]
  F1C["[id].js"]
  F2A["SearchFilters.jsx"]
  F2B["filterData.js"]
  F2C["search.js"]

  G1["assets/"]
  G2["components/"]
  G3["utils/"]
  G1A["images/"]:::sub
  G1B["house.jpg"]
  G1C["noresult.svg"]
  G2A["Footer.jsx"]
  G2B["Layout.jsx"]
  G2C["Navbar.jsx"]
  G3A["fetchApi.js"]

  E1["_app.js"]
  E2["index.js"]
  E3["search.js"]
  E4["property/"]
  
  A --> B
  A --> C
  A --> D
  A --> AB
  A --> AA
  A --> E
  A --> F
  A --> G
  A --> H

  F --> F1
  F --> F2
  F1 --> F1A
  F1 --> F1B
  F1 --> F1C
  F2 --> F2A
  F2 --> F2B
  F2 --> F2C

  G --> G1
  G --> G2
  G --> G3
  G1 --> G1A
  G1A --> G1B
  G1A --> G1C
  G2 --> G2A
  G2 --> G2B
  G2 --> G2C
  G3 --> G3A

  E --> E1
  E --> E2
  E --> E3
  E --> E4
```

---

## Directory Overview

- **domains/**:  
  Contains feature-specific logic, grouped by major business domains.  
  - `property/`: UI and logic for single property views and galleries.  
  - `search/`: Filtering, auto-complete, and search result logic.

- **shared/**:  
  Holds common elements shared by all domains.  
  - `components/`: Header, footer, layout, and other reusable UI pieces.  
  - `utils/`: Common data fetching and helpers.  
  - `assets/images/`: Central image storage.

- **pages/**:  
  Next.js page entrypoints; minimal business logic, instead delegate to domain/shared components.

- **kavia-docs/**:  
  Project architectural, analysis and documentation.

- **assets/, attachments/, figmafiles/**:  
  Reserved for external files, static assets, attachments, and design sources as needed.

- **next.config.js, package.json**:  
  Configuration, dependencies and project setup.

---

For migration help or component placement, see the README "Migration" section or reach out to the maintainers.

