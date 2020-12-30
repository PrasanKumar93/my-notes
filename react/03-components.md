# Components

## Points
- Components are like functions, Input is "props, state" , Output is "UI"
- Props are immutable (cannot be changed), states (internal) are mutable (can be changed)
- Style : Function components (prefer) / Class components
- **Smart DOM update** - uses diffing algorithm (by default), even if entire data is re-binded, only part of DOM is updated which has different HTML compared to earlier

```js
//function style

const Hello = (props) => {
   return(
       <div> Hello {props.title}! </div>
   );
}

const rootElement = document.getElementById("root");
ReactDOM.render(<Hello title="World" />, rootElement);

``` 

```js
//class style

class Hello extends React.Component {
  render() {
    return <div> Hello {this.props.title}! </div>;
  }
}

const rootElement = document.getElementById("root");
ReactDOM.render(<Hello title="World" />, rootElement);
``` 

- JSX is not HTML, it's converted to pure javascript check [Babel repl](https://babeljs.io/repl)
- For JSX syntax in js file, we must import React lib

```js
//above class style code in JS

class MyComponent extends React.Component {
  render() {
    return /*#__PURE__*/React.createElement("div", null, " Hello World! ");
  }

}
```

- Function/ Class names must start with capital to avoid conflict with browser HTML element.

```
React.render(<button/>,...) will call html button
React.render(<Button/>,...) will call js function
```

## Examples
### Hello world
- Hello world component

[Sandbox link](https://codesandbox.io/s/mystifying-hopper-lwntn)


<script src="https://gist.github.com/PrasanKumar93/efd9d23e34a6d92cd661d36992335160.js"></script>

### Button counter
- Button counter component using state

```js
//state syntax
//setter/getter can be any - number, string, array..etc
const [getterStateVal, setterFnStateVal] = useState(initialStateValue);

//onClick takes function reference
onClick={functionReference}
```

[Sandbox link](https://codesandbox.io/s/gifted-almeida-rmu0b)

<script src="https://gist.github.com/PrasanKumar93/94acf5af3ce27b50bcb3bfccd80b1ebf.js"></script>


### Multiple button counter

- Multiple button counter component using state

[Sandbox link](https://codesandbox.io/s/recursing-oskar-7b614)

[Gist link](https://gist.github.com/PrasanKumar93/bf571346b178f5662d845cce12d03554)


### Github cards

```js
function CardList(props) {
  return (
    <div className="card-list-container">
      {props.dataArr.map((elm) => {      {/*looping example, also child item must have unique key*/}
        return <Card key={elm.id} {...elm} />;        {/*spreading properties*/}
      })}
    </div>
  );
}
```

[Sandbox link](https://codesandbox.io/s/exciting-haze-i41ms?file=/src/index.js)

[Gist link](https://gist.github.com/PrasanKumar93/666dde7a1455805a15c9d6d7a1e576bb)


### Input elements

```js
  //controlled input (2-way)
  const [firstName, firstNameSetter] = useState();

   <TextBox value={firstName} valueSetter={firstNameSetter}
            placeholder="Enter First Name (controlled)"/>

  function TextBox(props) {
    const changeHandler = (evt) => {
        if (props.valueSetter) {
           props.valueSetter(evt.target.value);
        }
    };
    return (
        <input
        type="text"
        value={props.value}
        onChange={changeHandler}
        placeholder={props.placeholder}
        />
    );
 }          

```

```js
  //uncontrolled input (get value when needed)
  const lastNameElm = React.useRef(null);

  <TextBox2 refVal={lastNameElm}
            placeholder="Enter Last Name (uncontrolled)"/>

  function TextBox2(props) {
    return (
        <input
        type="text"
        value={props.value}
        ref={props.refVal}
        placeholder={props.placeholder}
        />
    );
 } 

 //access value from element (.current returns underlying html elment)
 let lastName = lastNameElm.current.value;           

```

```js

//immutable array example
const [arr, arrSetter] = useState([]);

arrSetter([...arr, newElm]);

```

[Sandbox link](https://codesandbox.io/s/dazzling-ritchie-z05j6?file=/src/index.js)

[Gist link](https://gist.github.com/PrasanKumar93/90c8e8c44e118767c1b61a469010e3ec)


```js
//in class style function alternate to hooks (getter/ setter) -> following setState style

constructor(){
    this.state = {
        userName:''
    }
}

someFunc(){
  this.setState({userName:'newVal'});
}
```

- Move all hooks in to custom hook function for better code maintenance


### useEffect() & key example

- think useEffect() like load() & it’s return function like unload() But useEffect() will run on every state change !!

```js
function Card(props) {
  React.useEffect(() => {
    console.log(props.login + " rendered");

    return () => {
      console.log(props.login + " unloaded");
    };
  });

  return (
    <div className="card">
     ...
    </div>
  );
}
```

- **when ever a state changes entire existing element gets re-rendered intelligently (virtual dom diff), but code gets re-executed**

```js
let oneTimeReLoad = false;
function CardList(props) {
  let [dataArr, dataArrSetter] = React.useState(props.dataArr);
  console.log("--CardList loaded--");

  if (!oneTimeReLoad) {
    setTimeout(() => {
      console.log("--time out--");

      let newArr = dataArr.map((itm) => {
        itm.name += " 1";
        return itm;
      });
      dataArrSetter(newArr); //so current CardList re-loaded
    }, 5000);
  }
  oneTimeReLoad = true;

  return (
    <div className="card-list-container">
      {props.dataArr.map((elm) => {
        return <Card key={elm.id} {...elm} />;  //repeating element needs key value
      })}
    </div>
  );
}

```

-  If key value changes, React will unmount the component & load  again as new component

- [sandbox link](https://codesandbox.io/s/condescending-cray-exqrl?file=/src/card.js)