# Project Foundation & Architecture

## Tech Stack & Architectural Purpose

- **React (Vite)**: Serves as our component-based UI layer, paired with Vite for fast hot-module replacement (HMR) and optimized production bundling.
- **react-router-dom**: Manages client-side navigation, nested layouts, dynamic URL parameters, and route-level access guards (e.g., separating public auth pages from protected application views).
- **axios**: Acts as our centralized HTTP client inside `src/api/axiosClient.js`. Used instead of native `fetch` to attach auth tokens automatically via request interceptors, standardize base URLs, and handle global API error responses (like `401 Unauthorized`) in one place.
- **zustand**: Provides lightweight, boilerplate-free global client state management (`src/store/`) for cross-component data such as authenticated user sessions, UI modals, and theme/sidebar states without prop drilling or heavy Redux setup.
- **formik**: Handles complex form state lifecycle—tracking input values, touched fields, submission states, and reset handlers consistently across login, registration, and data-entry screens.
- **yup**: Pairs directly with Formik (`validationSchema`) to enforce declarative, schema-based client-side validation rules and user-friendly error messages before API payloads are dispatched.
- **tailwindcss**: Provides utility-first styling powered by a centralized `@theme` design token system in `src/index.css`, ensuring strict visual consistency and preventing hardcoded colors, spacing, or radii in components.
- **react-icons**: Supplies lightweight, tree-shakeable SVG icons for navigation menus, form indicators, and status alerts without bloating the bundle.

## Design Token Rules

All colors, spacing values, border radii, and font sizes are defined in `src/index.css` under `@theme`. Do not use arbitrary values (e.g., `bg-[#123456]` or `p-[13px]`) in JSX components.
