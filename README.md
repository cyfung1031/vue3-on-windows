# vue3-on-windows
Vite + Vue3 + Router + TailwindCSS for Windows 7

* Your Project Path shall be without space

# Using Create-Vite-App (Old Way)

This is not recommended.

## Step 1 - Create Vite Vue3 Project using Create-Vite-App (Vite1)
Ref: https://segmentfault.com/a/1190000038999784
```
npm install -g create-vite-app
create-vite-app vue3-demo
cd vue3-demo
npm install
```
* Note: Don't use offical `npm init vite` as it has error for Windows 7 

## Step 2 - Install Vue-Router
```
npm info vue-router versions
npm install vue-router@4.0.11
```

## Step 3 - Install TailwindCSS
Ref: https://tailwindcss.com/docs/guides/vue-3-vite
```
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
npx tailwindcss init -p
```

## Step 4 - Files Editing

### ./src/main.js
```
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import './index.css'

createApp(App).use(router).mount('#app')
```

### ./src/router/index.js

```
import { createRouter, createWebHistory } from 'vue-router'
import Home from '../views/Home.vue'
import Contact from '../views/Contact.vue'

const routes = [
  {
    path: '/',
    name: 'Home',
    component: Home
  },
  {
    path: '/contact',
    name: 'Contact',
    component: Contact
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router

```

### ./src/index.css

```


/* ./src/index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

```

### ./tailwind.config.js

```
module.exports = {
  purge: ['./index.html', './src/**/*.{vue,js,ts,jsx,tsx}'],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}

```

# Vite2 (New Way)

This is recommended. Except scaffolding and vite.config.js, other shall be the same as Create-Vite-App (Vite1)

## Vite2's Scaffolding

```
npm init vite@latest 
cd vue3-demo
npm install esbuild@0.12.24
npm install
```

(esubild@0.12.26 is not stable, so force install 0.12.24 on your project folder before npm install)
(npm install will automatically download the neccessary packages)


## Configurations

### How to expose 'host' for external device display? #3396

https://github.com/vitejs/vite/discussions/3396

```
export default defineConfig({
  plugins: [vue()],
  server: {
    host: true
  }
})
```

### process is not defined

```
import { defineConfig } from 'vite'
// ... 
export default defineConfig({
    // ... 
    define: {
        'process.env': {}
    }
})
```

### isCustomElement

```
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue({
    template: {
      compilerOptions: {
        isCustomElement: tag => tag.startsWith('ion-')
      }
    }
  })],
  server: {
    host: true
  },
  port: 3000,
  define: { 
      'process.env': {}
  }
})
```

## Vue-i18n

```
npm install vue-i18n@next
```

8.x is not for Vue3
9.x is compatible with vue 3


### main.js

```
import { createI18n, useI18n } from 'vue-i18n'
```

## vue-router

```
npm install vue-router@4
```



# VS Code Extensions
* [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
* [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
* [PostCSS Language Support](https://marketplace.visualstudio.com/items?itemName=csstools.postcss)
