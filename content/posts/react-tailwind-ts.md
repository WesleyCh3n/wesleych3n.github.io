---
title: "React + Tailwind + Typescript"
date: 2021-12-22
categories:
  - note
tags:
  - typescript
toc: true
toc_label: "Outline"
toc_sticky: true
toc_icon: "box-open"

---

## Create React Typescript Project

```bash
yarn create react-app ./ --template typescript
```

## Install Tailwind in devDependency

```bash
yarn add -D tailwindcss postcss autoprefixer
# yarn add -D tailwindcss@npm:@tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
```

## Install CRACO
<details>
  <summary>No Need Anymore (skip)</summary>
```bash
yarn add @craco/craco
```

`package.json`
```json
"scripts": {
    "start": "craco start",
    "build": "craco build",
    "test": "craco test",
    "eject": "react-scripts eject"
},
```

`craco.config.js`

```javascript
module.exports = {
  style: {
    postcss: {
      plugins: [require("tailwindcss"), require("autoprefixer")],
    },
  },
};
```
</details>

## Generate `tailwind.config.js`

```bash
yarn tailwindcss init
```

`tailwind.config.js`
```javascript
module.exports = {
  purge: ["./src/**/*.{js,jsx,ts,tsx}", "./public/index.html"],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
};
```

## Add Tailwind

`index.css`
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## Create some components

`GradientText.tsx`
```typescript
type Props = {
  text: string;
};

export const GradientText = ({ text }: Props) => {
  return (
    <div className="p-10 min-h-screen flex items-center justify-center bg-cool-gray-700">
      <h1 className="text-9xl font-black text-white text-center">
        <span className="bg-gradient-to-r text-transparent bg-clip-text from-green-400 to-purple-500">
          {text}
        </span>
      </h1>
    </div>
  );
};
```

## Start

```bash
yarn start
```

