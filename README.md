# webpack-babel-react-boilerplate
Just read the title without the dashes ;)

## Quick Install
In order to save time and install it quicker you can copy this
```
 git clone git://github.com/lucascassiano/webpack-babel-react-boilerplate
 cd webpack-babel-react-boilerplate
```

### Config Babel
create file .babelrc
```
touch .babelrc
```
and then using a text editor add:
```
/* .babelrc */
{
    "presets":[
        "es2015", "react"
    ]
}

```

### Install dependencies and run
```
npm install && npm start
```
This boilerplate is running webpack 2, so you can change the default port to any number (usually higher than 1024)
```
npm start --port 80
```

### Compiling Bundle
```
npm run build
```
it will create an compiled app at ./dist
to serve it see the serving options bellow.

#References:
https://scotch.io/tutorials/setup-a-react-environment-using-webpack-and-babel

https://www.codementor.io/tamizhvendan/beginner-guide-setup-reactjs-environment-npm-babel-6-webpack-du107r9zr

# Advanced (slow) Install

## Create the project 
create the directory and init npm (define the project name, author etc..)
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
  template: './src/index.html',
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

## Babel setup
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


