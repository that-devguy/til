# Hot Module Replacement

**Hot Module Replacement (HMR)** exchanges, adds, or removes modules while an application is running, without a full reload. Speeding up development by:

- Retaining app state which is lost during a full reload.
- Saving valuable dev time by only updating what's changed.
- Instantly updates the browser when modifications are made CSS/JS in the source code.

*HRM is not intended for use in production.*

Guide for setting up **HRM** with Webpack:

1. Set up a new project or navigate to an existing project directory.

2. Install webpack and webpack-dev-server as development dependencies:
```shell
npm install --save-dev webpack webpack-dev-server
```

3. Create a `webpack.config.js`, in the project root. Configure the entry point and output path:
```javascript
const path = require('path');

module.exports = {
    entry: './src/index.js',
    out: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
    },
};
```

4. Add a `start` script to your `package.json` file:
```json
{
    "scripts": {
        "start": "webpack-dev-server --open"
    }
}
```

5. Run the dev server using `npm start`.

This will start the webpack dev server with HMR enabled. It will automatically open your default browser and serve the bundled application.

*Depending on your project's complexity and requirements, you may need to configure additional loaders, plugins, or tweak the webpack config to handle different file types and frameworks.*