# Github Explorer
Simple project in ReactJS for [RocketSeat Bootcamp](https://rocketseat.com.br/ignite).

## Setup first environment project
### Creating `package.json` file
```
yarn init -y
```
### Installing React
```
yarn add react react-dom
```

### Configuring Babel
* Install the dependencies:
```
yarn add @babel/core @babel/cli @babel/preset-env @babel/preset-react babel-loader -D
```
* Create the `babel.config.js` file:
```
module.exports = {
    presets: [
        '@babel/preset-env',
        ['@babel/preset-react', {
            runtime: 'automatic'
        }]
    ]
}
```
* To generate the `bundle.js` file, run `yarn babel src/index.jsx --out-file dist/bundle.js`

### Configuring Webpack
* Install the dependencies:
```
yarn add webpack webpack-cli webpack-dev-server -D
```
* Create the `webpack.config.js` file:
```
const path = require('path')

module.exports = {
    mode: 'development',
    entry: path.resolve(__dirname, 'src', 'index'),
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    resolve: {
        extensions: ['.js', '.jsx'],
    },
    module: {
        rules: [
            {
                test: /\.jsx$/,
                exclude: /node_modules/,
                use: 'babel-loader'
            }
        ]
    }
}
```
* To generate the `bundle.js`file, run `yarn webpack`.

## Directory structure
- public
    - index.html
- src
    - index.jsx
    - App.jsx
- dist
    - bundle.js

## Tutorials
* [Installing Yarn](https://classic.yarnpkg.com/en/docs/install)