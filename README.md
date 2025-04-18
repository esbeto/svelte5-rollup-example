# Svelte 5 Rollup Example

This project demonstrates how to build and export Svelte 5 components using Rollup. It showcases a pattern for bundling components into standalone JavaScript modules that can be used in various environments.

## About

This project is not a component library, but rather an educational example showing:

- How to configure Rollup for Svelte 5
- How to bundle components and their styles
- How to consume the compiled components

## Structure

- `src/lib/` - A folder to place your Svelte components
- `src/svelte.js` - Exports the Svelte 5 runtime
- `rollup.config.js` - Rollup configuration
- `index.html` - Example usage

## How It Works

### Rollup Configuration

The Rollup configuration automatically detects and builds all Svelte components in the `src/lib` directory. For each component:

- The component is compiled as an ES module
- Svelte's runtime is externalized
- CSS is extracted to a separate file
- Source maps are generated

### Using the compiled Components

#### In vanilla HTML/JS

```html
<!-- Include the component's CSS -->
<link rel="stylesheet" href="dist/component.css" />

<!-- Load the Svelte bundle -->
<script type="importmap">
  {
    "imports": {
      "svelte": "./dist/svelte.js",
      "svelte/internal/client": "./dist/svelte.js"
    }
  }
</script>

<!-- Set up the mount point -->
<div id="root"></div>

<!-- Import and mount the component -->
<script type="module">
  import { mount } from "svelte";
  import Component from "./dist/component.js";

  const app = mount(Component, {
    target: document.getElementById("root"),
    props: {
      // Your props here
    },
  });
</script>
```

## Extending This Example

To add new components:

1. Create a new `.svelte` file in the `src/lib` directory
2. Run the build command (see package.json) - Rollup will automatically detect and build all components

## About .svelte.js files

This example is not tested with `.svelte.js` files. If you want to use them, you'll probably need to modify the `rollup.config.js` file.

## License

This project is released into the public domain under the [Creative Commons Zero (CC0)](LICENSE) license. You are free to use, modify, and distribute the code without any restrictions.
