# FRONTEND-GUIDELINES

### HTML

### SCSS
  - Use variables defined for adding css such as padding, margin, font-size etc
  - for text/font use the defined mixins
  - define colors in a signle css file before using it in
  - if images can be converted to fonts, prefer that. ([icomooon](https://icomoon.io/) for converting images to fonts)

### JAVASCRIPT

### REACT JS

Project directory structure

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
└── src
    ├── actions
    │   ├── app-actions.js
    |   └── auth-actions.js
    |
    ├── assets
    |   ├── fonts
    |   └── images
    |
    ├── components
    |   └── auth-module
    |
    ├── contants
    |   └── action-type.js
    |
    ├── helpers
    |   └── auth-helpers.js
    |
    ├── i18n
    |   └── config.js
    |
    ├── reducer
    |   └── root.js
    |
    ├── routes
    |   └── routes.js
    |
    ├── store
    |   └── store.js
    |
    ├── styles
    |   └── app.scss
    |
    └── utils
        ├── app-api-utils.js
        └── string-utils.js
```

  - define common components in a different folder and use them instead of repeating code
  - use camel casing to define variables, constants and functions
  - define the text/string content into translation.json if its being used
  - define the constants in a different file before using eg: redux-action-types, value check for variable against a constant string
  - Import images into a constants file before using them in any componenets for display
  - define common helper functions/string utils under the utils folder so that it can be reused (eg: string mapping)
  - maintain indentations for easy readability
  - define view inside a react render metod if the render method is big
  - get the props, states that are needed in rendering into constants and use them inside the return instead of (this.props.xyz.abc.prq)


action type grammer - VERB_{action}_SUCCESS / VERB_{action}_FAILED
