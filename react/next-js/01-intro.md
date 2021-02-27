- https://nextjs.org/learn/basics/create-nextjs-app //check mandatory

- It's server side rendering than SPA (client side rendering) style

## Setup

```sh
npm init
npm install react react-dom next --save
```

- In package.json add scripts

```js
{
    dev:"next",
    build:"next build",
    start:"next start",
}
```

## File based routing

- folder structure

```js
/pages
  - index.js  (localhost:3000)
  - about.js  (localhost:3000/about)
/public
  /images     (localhost:3000/images/flowers.jpg)
```

- so page will contain any exported function returning JSX
