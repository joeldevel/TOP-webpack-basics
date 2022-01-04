# TOP-webpack-basics
Some basics on webpack setup

## contents

- How to install webpack?
- How do you load CSS using webpack?
- How do you load images using webpack?
- How do you load fonts using webpack?
- How do you load data using webpack?
- How would you track errors in bundled source code?
- How to use watch, hot server, etc?

### Installing webpack

```
    npm init -y 
    npm install webpack webpack-cli --save-dev
    mkdir dist && mdir src && touch src/index.js
```

Put your JS code in index.js. This is the default configuration: webpack takes that file to create a dependency graph

### load css
[link to documentation](https://webpack.js.org/guides/asset-management/#loading-css)

Install the loaders `npm install --save-dev style-loader css-loader`

Add this to the webpack.config.js file

```

module: {

    rules: [

      {

        test: /\.css$/i,

        use: ['style-loader', 'css-loader'],

      },

    ],

  },
```

### load images
[link to documentation](https://webpack.js.org/guides/asset-management/#loading-images)

Add this to the webpack.config.js file, under the module object, inside the rules array


```
     {

        test: /\.(png|svg|jpg|jpeg|gif)$/i,

        type: 'asset/resource',

      },
```


### how to track errors
[link to documentation](https://webpack.js.org/guides/development/#using-source-maps)

Install the html-webpack-plugin:

`npm install --save-dev html-webpack-plugin`

Import it in the webpack.config.js file:

`const HtmlWebpackPlugin = require('html-webpack-plugin');`

Add plugins to configuration with the following entries:

```
plugins: [

    new HtmlWebpackPlugin({

      title: 'Output Management',
      title: 'Development',

    }),

  ],
```

Add devtool entry:
```
devtool: 'inline-source-map',
```

### How to use watch, dev server, etc?

[link to documentation](https://webpack.js.org/guides/development/#using-watch-mode)
