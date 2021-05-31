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
yarn add webpack webpack-cli webpack-dev-server html-webpack-plugin cross-env style-loader css-loader node-sass sass-loader -D
```
* Create the `webpack.config.js` file:
```
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

const isDevelopment = process.env.NODE_ENV !== 'production'

module.exports = {
    mode: isDevelopment ? 'development' : 'production',
    devtool: isDevelopment ? 'eval-source-map' : 'source-map',
    entry: path.resolve(__dirname, 'src', 'index'),
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    resolve: {
        extensions: ['.js', '.jsx'],
    },
    devServer: {
        contentBase: path.resolve(__dirname, 'public')
    },
    plugins: [
        new HtmlWebpackPlugin({
            template: path.resolve(__dirname, 'public', 'index.html')
        })
    ],
    module: {
        rules: [
            {
                test: /\.jsx$/,
                exclude: /node_modules/,
                use: 'babel-loader'
            },
            {
                test: /\.scss$/,
                exclude: /node_modules/,
                use: ['style-loader', 'css-loader', 'sass-loader']
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
    - styles
        - global.scss 
    - index.jsx
    - App.jsx
- dist
    - bundle.js
    - index.html

## Running the project in developmmnet environment
```
yarn dev
```

## Compiling the project in production environment
```
yarn build
```

## Tutorials
* [Installing Yarn](https://classic.yarnpkg.com/en/docs/install)