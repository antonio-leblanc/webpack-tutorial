# Webpack-tutorial

- [Design Course - Youtube](https://www.youtube.com/watch?v=TzdEpgONurw)

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
    ...
    "dev": "webpack serve"
  }
```
and `npm run dev`