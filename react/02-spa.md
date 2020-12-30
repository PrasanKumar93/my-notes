## To use as SPA (web app)
- **View** : ReactJS
- **Router** : React router
- **State management** : Redux (centralized state) / Mobx (Observable state)
- **Http** : Fetch/ Axios
- **i18n** : react-intl
- **Form validation** : react-forms
- **Testing** : Jest
- **CLI** : create-react-app
- **Server side rendering** : Next.js

- **Animation** : react-motion
- **Others** : GraphQL

- Note : 
  - appropriate versions must be used together (use code mod to fix API issues)
  - [react starter projects](https://www.javascriptstuff.com/react-starter-projects/)


## UI Tests
- Run in memory via node (without browser)
- Fast & less config
- [Tools recommended](https://reactjs.org/docs/testing.html) : Jest and  React Testing Library (helpers)

## Points

### HTML VS JSX

```
| HTML                 | JSX                      |
|----------------------|--------------------------|
| for                  | htmlFor                  |
| class                | className                |
| <!-- comment-->      | {/* comment */}          |
| <style color="blue"> | <style={{color:'blue'}}> |
```

- JSX: javascript naming style and preventing conflict with reserved keywords

- convert html to JSX
  - online tools like [htmltojsx](https://magic.reactjs.net/htmltojsx.htm)
  - npm package : htmltojsx


### Old & new syntax while searching online

| old                             | New                                                           |
|---------------------------------|---------------------------------------------------------------|
| import {render} from 'react'    | import {render} from 'react-dom'                              |
| React.createClass               | var crc = require('create-react-class')                       |
| import {PropTypes} from 'react' | import {PropTypes} from 'prop-types' (use typescript instead) |
| mixins:[mixinName]              | Hooks                                                         |


### Use function component rather than class

```
//style 1 (popular) better with hooks
function Greeting() {
 return <h1>Hello, world</h1>;
}

//style 2
class Greeting extends Component {
 render() {
   return <h1>Hello, world</h1>;
 }
}
```
### Use type script instead flow or PropTypes


### React renderers

- react-dom , react-native, react-vr


### Unix philosophy


<blockquote>
"Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface" by Doug Mcllroy
</blockquote>

### JS Tips
- Use map, filter & reduce instead for/while loop in JSX (not a hard rule but recommendation)
- **Rule of hooks** : Don't call hooks inside a loop or condition

### Editor
- Use 'prettier' extension in VSCode with "Format on save" enabled in editor settings