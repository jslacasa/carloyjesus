# Project Overview: Quartz v4

Quartz v4 is a static site generator designed for publishing digital gardens and notes as a website. It leverages a modern TypeScript/Node.js stack, using Preact for rendering, `esbuild` for bundling, and a rich plugin architecture for content transformation and emission. The project provides a command-line interface (CLI) for building, serving, creating, updating, and syncing the website.

## Building and Running

The Quartz project uses a CLI tool to manage various operations. The primary commands are `build` and `serve`.

**Prerequisites:**

*   Node.js (version 22 or higher)
*   npm (version 10.9.2 or higher)

**Key Commands:**

*   **Install Dependencies:**
    ```bash
    npm install
    ```
*   **Build the website:**
    This command compiles your markdown content and other assets into a static website in the `public` directory (by default).
    ```bash
    npx quartz build
    ```
    *   `--output` or `-o`: Specify the output folder (default: `public`).
    *   `--concurrency`: Number of threads to use to parse notes.
*   **Build and Serve Locally (with live-reloading):**
    This command builds the website and then starts a local development server, watching for changes and rebuilding automatically.
    ```bash
    npx quartz build --serve
    ```
    *   `--port`: Port to serve Quartz on (default: `8080`).
    *   `--wsPort`: Port for WebSocket-based hot-reload (default: `3001`).
    *   `--baseDir`: Base path to serve your local server on.
*   **Watch for changes and rebuild automatically (without serving):**
    ```bash
    npx quartz build --watch
    ```
*   **Create a new Quartz project:**
    This command initializes a new Quartz project, allowing you to choose a setup strategy (empty, copy from existing, or symlink to existing) and configure markdown link resolution.
    ```bash
    npx quartz create
    ```
    *   `--directory` or `-d`: Specifies the content directory (default: `content`).
    *   `--source` or `-s`: Source directory to copy/create symlink from.
    *   `--strategy` or `-X`: `new`, `copy`, or `symlink` for content folder setup.
    *   `--links` or `-l`: Strategy to resolve links (`absolute`, `shortest`, `relative`).
*   **Update Quartz:**
    This command pulls the latest updates from the Quartz upstream repository and updates dependencies.
    ```bash
    npx quartz update
    ```
*   **Sync with Git:**
    This command allows you to commit, pull, and push changes to your Git repository.
    ```bash
    npx quartz sync
    ```
    *   `--commit`: Create a Git commit for unsaved changes (default: `true`).
    *   `--message` or `-m`: Custom commit message.
    *   `--push`: Push updates to your Quartz fork (default: `true`).
    *   `--pull`: Pull updates from your Quartz fork (default: `true`).
*   **Check code formatting and types:**
    ```bash
    npm run check
    ```
*   **Format code:**
    ```bash
    npm run format
    ```
*   **Run tests:**
    ```bash
    npm run test
    ```

**Docker:**

The project can be run in a Docker container. The `Dockerfile` uses a multi-stage build process. The default command in the Docker image is `npx quartz build --serve`.

## Development Conventions

*   **Language:** TypeScript
*   **UI Framework:** Preact
*   **Styling:** SCSS
*   **Code Formatting:** Prettier (enforced by `npm run check` and applied by `npm run format`).
*   **Type Checking:** TypeScript (enforced by `npm run check`).
*   **Configuration:**
    *   `quartz.config.ts`: Main configuration for the Quartz site, including page title, locale, base URL, ignore patterns, theme (typography and colors), and plugin setup (transformers, filters, emitters).
    *   `quartz.layout.ts`: Defines the component-based layout for different page types (shared, content, list).
*   **Git Branching:** The `handleUpdate` function suggests interaction with an `upstream` remote and `QUARTZ_SOURCE_BRANCH`, indicating a fork-based workflow for contributions.
*   **Community:** The `CODE_OF_CONDUCT.md` outlines behavioral expectations for contributors, promoting an inclusive environment.
