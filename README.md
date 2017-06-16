# webpack-babel-react-boilerplate
Just read the title without the dashes ;)

https://scotch.io/tutorials/setup-a-react-environment-using-webpack-and-babel

https://www.codementor.io/tamizhvendan/beginner-guide-setup-reactjs-environment-npm-babel-6-webpack-du107r9zr

Create the project
```
mkdir myApp
cd myApp
npm init
```

## 1. Install Webpack and Webpack server

```
npm install --save-dev webpack webpack-dev-server path
```
Also, install html-webpack-plugin

```
npm install --save html-webpack-plugin

```

## 2. Create webpack.config.js file with the content (you can use $touch webpack.config.js)
```javascript
/*
    ./webpack.config.js
*/
const path = require('path');

const HtmlWebpackPlugin = require('html-webpack-plugin');
const HtmlWebpackPluginConfig = new HtmlWebpackPlugin({
  template: './client/index.html',
  filename: 'index.html',
  inject: 'body'
})

module.exports = {
  entry: './client/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  watchOptions: {
  aggregateTimeout: 300,
  poll: 1000,
  ignored: /node_modules/
},
/*
  devServer: {
  contentBase: path.resolve( "public"),
  compress: true,
  port: 9000
},*/
performance: {
  hints: false
},
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test: /\.jsx$/, loader: 'babel-loader', exclude: /node_modules/ }
    ]
  },
  plugins: [HtmlWebpackPluginConfig]
}

```


## Babel config
```
babel-loader babel-core babel-preset-es2015 babel-preset-react
```
create './.babelrc'
```
touch .babelrc
```
and add on it:
```
{
    "presets":[
        "es2015", "react"
    ]
}
```

## Serve dist
```
npm run build
```
if you don't have Serv installed

```
npm install -g serve
serve -s dist
```

to serve for production you can use pm

```
npm instal -g pm2

sudo pm2 start serve --name "myapp" -- -s build
```

## Fast Track
In order to save time and install it quicker you can copy this
```
 git clone git://github.com/lucascassiano/webpack-babel-react-boilerplate
```
create file
