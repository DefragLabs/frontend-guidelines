## JS guidelines

### Define common components in a different folder and use them instead of repeating code

This ensures we don't have any duplicate code lying around. A good example might be a `modal-component`, which can be reused.

### Use camel casing to define variables, constants and functions

Camel case variable name.
```
var firstName = "Nate";
```

Constants
```
const itemsPerPage = 50;
```

Use constants when a variable is fixed.

Functions
```
function getUserDetails() {
  ...
}
```

### Define the text/string content into translation.json if its being used

**Filepath:** `public/local/en/translations.json`

**Dependencies:**
```
"i18next": "^11.3.3",
"i18next-browser-languagedetector": "^2.2.0",
"i18next-xhr-backend": "^1.5.1",
"react-i18next": "^7.7.0",
```

**Example:**
```
// translations.json
{
  "header": {
    "login": "Login",
    "customerLogin": "Customer login",
    "signUp": "Sign up",
    "logout": "logout"
  },
  "auth": {
    "emailAddress": "EMAIL ADDRESS",
    "password": "PASSWORD",
    "confirmPassword": "CONFIRM PASSWORD",
    "enterEmail": "ENTER EMAIL",
  }
}
```

### Define the constants in a different file before using 

If the constants need to be accessed in multiple files, it is good to move those constants to a common file.
**Example**: redux-action-types, value check for variable against a constant string


### Import images into a constants file before using them in any components

**FilePath:** `src/constants/images.js`

**Example:**
```
// images.js
import brandLogoHeader from  '../assets/images/brand-logo-header.png';
import brandLogoFooter from  '../assets/images/brand-logo-footer.png';

// Variables
export const BRAND_LOGO_HEADER = brandLogoHeader;
export const BRAND_LOGO_FOOTER = brandLogoFooter;
```

Use `BRAND_LOGO_HEADER, BRAND_LOGO_FOOTER` in components.

### Define common helper functions/string utils under the utils folder.

**Example:**
```
// string-utils.js
export function removeSlash(string) {
  return string.replace(/\//g, '');
}
```

These are common utilities, which will be used throughout the code.

### Code indentation

We use 2 spaces for indentation. Also use code blocks properly.

**Example:**
```
function getUserDetails(users, userID) {
  for(var i=0; i < users.length, i++) {
    var user = users[i];
    if(user.ID === userID) {
      return user;
    }
  }
}
```

We can see that code inside `for` & `if` is further indented.

### Don't overload react render method with too much code.

Split the code into disparate functions and reference them in the render method.

**Example:**
```
render() {
  return (
    <div className="user-list">
      {this.getUserTable()}
    </div>
  )
}
```

### Get the props, states that are needed in rendering into constants

```
// Good
const { users, orgs } = this.props;

// Bad
const users = this.props.users;
cont orgs = this.props.orgs;
```

### Action type grammer

`VERB_{action}_SUCCESS / VERB_{action}_FAILED`

```
ATTEMPT_LOGIN
RECEIVE_LOGIN_SUCCESS
RECEIVE_LOGIN_FAILED
```
### Don't call child's methods in parent's component

1. This pattern breaks the encapsulation of both the parent and child. The child cannot be refactored without carefully checking if its public methods are used elsewhere. The parent cannot be tested in isolation without injecting its dependencies (i.e. the child)
2. In general, data should be passed down the tree via props. There are a few exceptions to this (such as calling .focus() or triggering a one-time animation that doesn’t really “change” the state) but any time you’re exposing a method called “set”, props are usually a better choice. 

### Cache busting 

All of our apps are bootstarped with [CRA](https://facebook.github.io/create-react-app) and CRA adds hash to JS and CSS files during build process. Incase browser is caching `index.html` itself and because of that users are not able to see latest changes after deployment then below are the solutions to solve cacheing problem for the appications which are bootstraped using [CRA](https://facebook.github.io/create-react-app).

1. By unregistering web workers

* `import { unregister } from './registerServiceWorker';`

* Call `unregister()` in `index.js` filed instead of `registerServiceWorker()`.

2. Adding "Cache-Control": "no-store, no-cache" line to server side response header only for index.html location.
