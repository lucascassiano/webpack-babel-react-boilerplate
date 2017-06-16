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

## WebPack setup

```
npm install --save-dev webpack webpack-dev-server path
```



```
npm install --save html-webpack-plugin
```

## Babel config
```
babel-loader babel-core babel-preset-es2015 babel-preset-react
```
create '.babelrc'
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
npm install -g serve
serve -s dist
```
