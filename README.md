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
yarn add @types/react @types/react-dom -D
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
yarn add webpack webpack-cli webpack-dev-server html-webpack-plugin cross-env style-loader css-loader node-sass sass-loader @pmmmwh/react-refresh-webpack-plugin react-refresh -D
```
* Create the `webpack.config.js` file:
```
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')
const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin')

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
        extensions: ['.js', '.jsx', '.ts', '.tsx'],
    },
    devServer: {
        contentBase: path.resolve(__dirname, 'public'),
        hot: true
    },
    plugins: [
        isDevelopment && new ReactRefreshWebpackPlugin(),
        new HtmlWebpackPlugin({
            template: path.resolve(__dirname, 'public', 'index.html')
        })
    ].filter(Boolean),
    module: {
        rules: [
            {
                test: /\.(j|t)sx$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader',
                    options: {
                        plugins: [
                            isDevelopment && require.resolve('react-refresh/babel')
                        ].filter(Boolean)
                    }
                }
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

### Configuring Typescript
* Install the dependencies:
```
yarn add typescript @babel/preset-typescript -D
```
* Initialize the typescript
```
yarn tsc --init
```
* Update tsconfig.json
```
{
  "compilerOptions": {
    "lib": ["dom", "dom.iterable", "esnext"], /* add DOM HTML */
    "allowJs": true, /* allow js and ts files */
    "jsx": "react-jsx", /* use react jsx */
    "noEmit": true, /* ommit code on build */
    "strict": true, /* strict javascript mode */
    "moduleResolution": "node",
    "resolveJsonModule": true, /* import json files */
    "isolatedModules": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src"]
}
```
* Update babel.config.js
```
    presets: [
        ...
        '@babel/preset-typescript',
        ...
    ]
```
* Update webpack.config.js


## Directory structure
- public
    - index.html
- src
    - components
        - RepositoryItem.jsx
        - RepositoryList.jsx
    - styles
        - global.scss
        - repositories.scss 
    - index.tsx
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