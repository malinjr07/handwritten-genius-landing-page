# Handwritten Genius

A modern web application built with SvelteKit and Tailwind CSS.

## Project Structure

### Source Directory (`/src`)

- `app.d.ts` - TypeScript type definitions
- `app.html` - Main HTML template

### Library (`/src/lib`)

- `components/` - Reusable UI components
  - `common/` - Common UI components (aliased as `@common`)
  - `core/` - Core UI components (aliased as `@core`)
  - `svg/` - SVG components (aliased as `@svg`)
- `images/` - Image assets
- `utils/` - Utility functions and helpers
  - `services/` - API and service integrations (aliased as `@services`)
  - `store/` - Application state management (aliased as `@store`)
  - `types/` - TypeScript type definitions (aliased as `@types`)

### Routes (`/src/routes`)

- `+layout.svelte` - Root layout component
- `+layout.ts` - Root layout logic
- `+page.svelte` - Home page component
- `defaults/` - Default route components

## Import Aliases

The project uses the following import aliases defined in `svelte.config.js`:

| Alias       | Path                        | Description                  |
| ----------- | --------------------------- | ---------------------------- |
| `@common`   | `src/lib/components/common` | Common UI components         |
| `@core`     | `src/lib/components/core`   | Core UI components           |
| `@svg`      | `src/lib/components/svg`    | SVG components               |
| `@services` | `src/lib/utils/services`    | API and service integrations |
| `@store`    | `src/lib/utils/store`       | Application state management |
| `@types`    | `src/lib/utils/types`       | TypeScript type definitions  |

## Development

### Prerequisites

- Node.js
- Yarn

### Setup

```sh
yarn install
```

### Running the development server

```sh
yarn dev
```

### Building for production

```sh
yarn build
```

### Previewing production build

```sh
yarn preview
```

## Styling

This project uses [Tailwind CSS](https://tailwindcss.com/) for styling. All custom styles should be added to the appropriate component using Tailwind's utility classes.
