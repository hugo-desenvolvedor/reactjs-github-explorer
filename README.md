# Github Explorer
Simple project in ReactJS for [RocketSeat Bootcamp](https://rocketseat.com.br/ignite).

## Setup first environment project
### Creating `package.json` file
```
yarn init -y
```
### Installing React
```
yarn add react
yarn add react-dom
```

### Configuring Babel
* Install babel dependencies:
```
yarn add @babel/core @babel/cli @babel/preset-env @babel/preset-react -D
```
* Create the `babel.config.js` file:
```
module.exports = {
    presets: [
        '@babel/preset-env',
        '@babel/preset-react'
    ]
}
```
* To convert a specific file:
```
yarn babel src/index.jsx --out-file dist/bundle.js
```

## Directory structure
- public
    - index.html
- src
    - index.jsx
- dist
    - bundle.js

## Tutorials