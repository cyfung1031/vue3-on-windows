# vue3-on-windows
Vite + Vue3 + Router + TailwindCSS for Windows 7

* Your Project Path shall be without space


# Step 1 - Create Vite Vue3 Project using Create-Vite-App
Ref: https://segmentfault.com/a/1190000038999784
```
npm install -g create-vite-app
create-vite-app vue3-demo
cd vue3-demo
npm install
```
* Note: Don't use offical `npm init vite` as it has error for Windows 7 

# Step 2 - Install Vue-Router
```
npm info vue-router versions
npm install vue-router@4.0.11
```

# Step 3 - Install TailwindCSS
Ref: https://tailwindcss.com/docs/guides/vue-3-vite
```
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
npx tailwindcss init -p
```

# Step 4 - Files Editing

## ./src/main.js
```
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import './index.css'

createApp(App).use(router).mount('#app')
```

## ./src/router/index.js

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

## ./src/index.css

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

## ./tailwind.config.js

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

## VS Code Extensions
* [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
* [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
* [PostCSS Language Support](https://marketplace.visualstudio.com/items?itemName=csstools.postcss)
