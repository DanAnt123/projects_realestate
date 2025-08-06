# Real Estate App

![Real Estate](https://i.ibb.co/jTW4bFC/image.png)

---

## Migration to Domain Driven Design (DDD) Folder Structure

**In May 2024 this project was migrated to a Domain Driven Design (DDD) folder structure. The major changes introduced:**

- Feature code is now grouped by domain under the `domains/` directory (e.g., `domains/property`, `domains/search`).
- Shared UI components, assets, and utilities are placed under the `shared/` folder for reuse across all domains.
- Page files in `pages/` now delegate domain-specific logic to corresponding components in `domains/`.
- This structure improves scalability, collaboration, and code maintainability by promoting explicit boundaries between features.

**How to migrate your own changes/customizations:**

1. Move all feature-specific logic (components, data, queries) to a subfolder of `domains/` by feature name.
2. Place any truly shared components, images, or utilities into `shared/components/`, `shared/assets/`, or `shared/utils/`.
3. Update all imports to use the new locations, especially in `pages/`, which should now import and compose from domain and shared modules.

For any issues, see the folder diagram in `kavia-docs/architecture.md`.

---

### [🌟 Become a top 1% Next.js 13 developer in only one course](https://jsmastery.pro/next13)
### [🚀 Land your dream programming job in 6 months](https://jsmastery.pro/masterclass)
