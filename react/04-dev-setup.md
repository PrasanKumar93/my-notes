# Development environment setup

## Create React App
- [create-react-app site](https://create-react-app.dev/)

```sh
npx create-react-app my-app
cd my-app
npm start
```
- so using npx, no need to install & maintain particular version of cli , it always takes latest package from npm source & executes commands on it

### Custom template

```sh
## syntax
npx create-react-app my-app --template [template-name]

## example
npx create-react-app my-app --template typescript
```

- [Available templates](https://www.npmjs.com/search?q=cra-template-*)

### Use

Inside the newly created project, you can run some built-in commands:

```sh
## Runs the app in development mode. Open http://localhost:3000 to view it in the browser.
npm start

## By default, runs tests related to files changed since the last commit.
npm test

## Builds the app for production to the build folder
npm run build

## Ejects all JS (eco system) config files for self handling 
npm run eject
```

## Own dev environment
- [jscomplete](https://jscomplete.com/learn/1rd-reactful)