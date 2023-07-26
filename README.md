# ClaudiaTestStyles - Vue 3 and Less Package

This package includes reusable styles and assets for Vue 3 projects, built with Less for flexibility and customization.

## Getting Started

Before you start, ensure you have Node.js and npm installed on your system. If they're not installed, you can download Node.js from the official website which comes bundled with npm.

## Installation

To use the claudiateststyles package in your Vue project, install it using npm:

```bash
npm install claudiateststyles --save
```

You also need to install the less and less-loader packages, which are required to compile and use Less in your Vue project:

```bash
npm install --save-dev less less-loader
```

## Vite Configuration

If you're using Vite, you need to configure it to compile Less. To do this, add the following configuration in your vite.config.js:

```javascript
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";
import vueJsx from "@vitejs/plugin-vue-jsx";
import copy from "rollup-plugin-copy";

export default defineConfig({
  plugins: [
    vue(),
    vueJsx(),
    copy({
      targets: [
        {
          src: "node_modules/claudiateststyles/src/assets/images/*",
          dest: "public/images",
        },
        {
          src: "node_modules/claudiateststyles/src/fonts/*",
          dest: "public/fonts",
        },
        {
          src: "node_modules/claudiateststyles/src/styles/styles.less",
          dest: "public",
        },
      ],
      hook: "writeBundle",
    }),
  ],
  resolve: {
    alias: {
      "@": "/src",
    },
  },
});
```

This configuration requires the rollup-plugin-copy package, which you can install with npm:

```bash
npm install --save-dev rollup-plugin-copy
```

## Usage

After you've installed and configured the claudiateststyles package, you can start using the styles and assets in your Vue components.

To use the styles in a component, import styles.less:

```vue
<style lang="less" scoped>
@import "/public/styles/styles.less";
// Your component styles here
</style>
```

To use the assets in a component, import the asset from the public folder:

```vue
<template>
  <img src="/public/images/logo.png" />
</template>
```
