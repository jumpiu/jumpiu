---
title: webpack basic
top_img: false
date: 2018-08-20 14:08:06
tags:
    - webpack
categories:
    - webpack
---

## Init
* mkdir webpack-demo && cd webpack-demo
* npm init -y   (-y  means skip questionnaire)
* create index.html, ./src/index.js
* remove main in package.json
* use import for 'lodash' instead of `<script src='...'>`, modify index.js,  index.html
* install webpack
    * local install (recommand)
Installing locally is what we recommend for most projects. This makes it easier to **upgrade projects individually** when breaking changes are introduced. 
Typically webpack is run via one or more npm scripts which will look for a webpack installation in your local node_modules directory.
            ```yarn add webpack webpack-dev-server```   or   
             ```npm install --save-dev webpack ```    or
             ```npm install --save-dev webpack@<version>```
    * global install
                ```yarn global add webpack webpack-dev-server```  or  
                ```npm install --global --save-dev webpack ```

* install webpack CLI 
   if install webpack v4 or later, then need to install webpack CLI  (Command Line Interface), you can choose one of the following.
     * webpack-cli  -- original full-featured webpack CLI,  ```npm install --save-dev webpack-cli```
     * webpack-command  -- lightweght CLI, ```npm install --save-dev webpack-command```

## use webpack
`npx webpack`    or 
add script in package.json, as below
```
"scripts": {
"build": "webpack"
},
```

### default
* entry    ./src/index.js
* output
    * filename: ./dist/main.js
    * path: ./dist
 `webpack src/index.js  dist/main.js`

### webpack config
* cretate webpack.config.js   `touch webpack.config.js`
默认情况下，webpack自动读取项目根目录下的webpack.config.js文件（如果有的话）作为配置内容
`webpack src/index.js --config config/webpack.config.js`
`webpack --config config/webpack.config.js`

* entry
    * entry 定义了入口文件，指定了webpack应该从哪个module开始build dependency graph （包含entry point 依赖的其他module 及libraries
    * single entry :  `entry: './src/index.js'`
    * multiple entry: 
```
entry: {
main: './src/index.js',
footer: './src/footer.js',
}
```
* output
        only one output configration is specified, even though there can be multiple entry points
    * filename      [name]/[hash]/[chunkhash]/[id].bundle.js  ("/" means "OR")
    * path   need be absolute path











