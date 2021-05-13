# Webpack-tutorial

- [Design Course - Youtube](https://www.youtube.com/watch?v=TzdEpgONurw)
- [Fireship IO - Youtube](https://www.youtube.com/watch?v=5IG4UmULyoA)

![img](https://miro.medium.com/max/3132/1*OEPInRk3XE-H7Nmv3FOnoQ.png)
### Steps

1. Init: `npm init`
2. Install dependencies: `npm i -D webpack webpack-cli`
3. Add build in scripts
```
  "scripts": {
    "build": "webpack"
  },
```

4. To render HTML `npm i -D html-webpack-plugin html-loader`
5. Create `webpack.config.js`
```
const HtmlWebPackPlugin = require('html-webpack-plugin');

module.exports = {
  module: {
    rules: [
      {
        test: /\.html$/,
        use: [
          {
            loader: 'html-loader',
            options: {minimize:true}
          },
        ]
      },
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({
      template: './src/index.html',
      filename: './index.html',
    })
  ]
}
```
6. Build `npm rum build` -> open index.html from /dist folder

7. Dev serve -> `npm i -D webpack-dev-server`. Then add to scripts in package.json
```
  "scripts": {
    "build": "webpack",
    "dev": "webpack serve"
  }
```
and `npm run dev`

8. Bundler Analyser:
- run `npm install --save-dev webpack-bundle-analyzer`
- follow the docs on the [npm package](https://www.npmjs.com/package/webpack-bundle-analyzer) to use it as a plugin in webpack.config.js
- run `npm run build --prod --stats-json` (or add as a script in package.json)
```
"scripts": {
  "build": "webpack",
  "dev": "webpack serve",
  "bundle-analyser": "npm run build --prod --stats-json"
},
```

9. SCSS loaders and plugins:
- install libs `npm i -D node-sass style-loader css-loader sass-loader mini-css-extract-plugin`
- add rule to module.exports in webpack.config

````
...
{
  test: /\.scss$/,
  use: [
    'style-loader',
    'css-loader',
    'sass-loader',
  ]
},
```
- add `MiniCssExtractPlugin` in module.exports
