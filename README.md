# FRONTEND-GUIDELINES

### HTML

### SCSS
  - Use varibales defined for adding css such as padding, margin, font-size etc
  - for text/font use the defined mixins
  - define colors in a signle css file before using it in
  - if images can be converted to fonts beofre using then use it(icomooon)

### JAVASCRIPT

### REACT JS
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
