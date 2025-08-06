# Onboarding Guide: Domain Driven Design (DDD) Structure for projects_realestate

Welcome to the `projects_realestate` Next.js codebase! This guide helps new and existing team members understand, navigate, and contribute effectively to the project’s Domain Driven Design (DDD) folder structure.

---

## Why Domain Driven Design (DDD)?

Domain Driven Design is an architectural approach for larger codebases and teams, where all business logic and related files are grouped by "domain" (or feature area). In this real estate app:

- **Domains** are major feature areas (e.g., property listings, search/filter logic).
- **Benefits:** DDD helps *scale* as new features are added, keeps feature code isolated to reduce accidental cross-contamination, makes onboarding smoother, and supports multiple teams or contributors working in parallel.
- It encourages separation of concerns, making it easier to maintain, extend, and test the codebase as your application grows.

---

## Major Folders and Domains

### `/domains/`

- **Purpose:** Houses all business logic and UI tied to a specific feature/domain.
- **Subfolders in this project:**
  - **property/**: All components and logic for displaying single properties, property image galleries, and details.
  - **search/**: Filtering UIs, search/filter logic, and configuration data for searching properties.
- **How to Extend:** New major features (e.g., "user", "favorites") would get their own folder here.

### `/shared/`

- **Purpose:** Anything reusable across domains—like header/footer/layout components, utility functions, and images.
- **Subfolders:**
  - **components/**: Core UI pieces used throughout (e.g., `Footer.jsx`, `Navbar.jsx`, `Layout.jsx`).
  - **assets/images/**: Project-wide images (e.g., house placeholder, no-results SVG).
  - **utils/**: Site-wide helpers (e.g., `fetchApi.js` for API calls).

### `/pages/`

- **Purpose:** Next.js page entrypoints—keep these as thin as possible.
- **Pattern:** Each page (e.g., `index.js`, `search.js`, `property/[id].js`) should mostly import from the relevant `domains/` and/or `shared/` folder.

### `/kavia-docs/`

- Architecture, audit reports, static analysis, and onboarding documentation lives here.

---

## How to Find/Add/Edit Features

- **Add new logic/UIs related to existing features:** Place them in the appropriate subfolder of `domains/`, keeping business logic with its feature.
  - Example: To add a new filter type to property search, edit or add code in `domains/search/`.
  - Example: To add a new property card type, work in `domains/property/`.
- **Add shared utilities or UI widgets:** Put them in `shared/`.
  - Example: Universal loading spinner → `shared/components/`.
  - Example: Helper to parse prices → `shared/utils/`.
- **Add a new page/route:** Use `/pages/`, then delegate to domains/shared wherever possible.
  - Example: `/pages/about.js` → Should render a shell and import most logic from `/domains/about` or `shared/`.

---

## Old vs. New Locations (Mapping Examples)

| Old Location         | New DDD Location            | Example                |
|----------------------|----------------------------|------------------------|
| `/components/Card.js`      | `/domains/property/Property.jsx`   | Feature-specific listing card |
| `/components/Footer.js`    | `/shared/components/Footer.jsx`    | Universal footer (shared)     |
| `/utils/fetchApi.js`       | `/shared/utils/fetchApi.js`        | Shared fetching logic         |
| `/public/images/noresult.svg` | `/shared/assets/images/noresult.svg` | All global images             |

---

## Code/Import Conventions

- **Import order:** Prefer importing from `"shared/..."` or the same domain.
- **No cross-domain imports:** `property/` must not import from `search/` and vice versa.
- **Pages (`/pages/`)**: Should only act as routes and shell components, importing most UI/logic from the relevant domain and shared folders.
- **Naming:** File names are typically PascalCase for React components (e.g., `Property.jsx`), camelCase for utilities (e.g., `fetchApi.js`).

---

## Adding New Features: Step-by-Step Example

**Suppose you want to add a 'Favorites' feature:**
1. Create `/domains/favorites/` and start with a `Favorites.jsx` for the root UI.
2. Place any API helpers in `/domains/favorites/fetchFavorites.js`.
3. Any "favorites" button needed globally? Make it reusable—`shared/components/FavoriteButton.jsx`.
4. Add a new page `/pages/favorites.js`, which imports the UI from `domains/favorites/Favorites.jsx`.

---

## Quickstart Tips

- Make sure to follow the import patterns — never reach across domains.
- Need to use a component project-wide or across multiple domains? Move it to `/shared/components/`.
- Only images in `/shared/assets/images/` are guaranteed to be available everywhere.
- Keep API endpoints, credentials, and config out of feature folders—put helpers in `shared/utils`, and load keys from environment variables.
- When in doubt, discuss structure questions with project maintainers!

---

## FAQ

**Q: What goes in "shared/" vs "domains/?"**  
A: Shared is for universal helpers, components, and assets. Domains are for feature-specific code.

**Q: Can I still use Next.js dynamic routing?**  
A: Yes! Your page file under `/pages/` can route to anything, but delegate logic to domains/shared.

**Q: Is this structure required for small changes?**  
A: Yes—consistency keeps the codebase maintainable over time.

**Q: Who to contact for architectural questions?**  
A: See `kavia-docs/architecture.md`, or ask the project maintainer listed in the contributors section of the repository.

---

Welcome, and happy coding in the DDD-powered `projects_realestate` app!
