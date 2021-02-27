## Component abstractions

- **HOC** : Higher order component [Link](https://reactjs.org/docs/higher-order-components.html)
  It's a function that takes a component & returns a new component
- **RP** : Rendered Prop
  A component with rendered prop takes a function that returns a react element & calls it instead of implementing it's own rendering logic
- **Context API**
  It is used to shared data that can be considered global to all component descendants in the component tree

  ```js
  //context API example

  //file : src/sample-context.js
  const SampleContext = React.createContext({});
  export { SampleContext };

  //file: src/components/card-list.js (parent component)
  import { SampleContext } from "src/sample-context.js";
  const CardList = () => {
    return (
      <SampleContext value={someData}>
        //so someData is available in child component
        <Card prop1={} />
        <Card2 prop1={} />
      </SampleContext>
    );
  };

  //file: src/components/card.js (child component)
  import { SampleContext } from "src/sample-context.js";
  const Card = () => {
    let myData = React.useContext(SampleContext); //myData can be used

    return <div>some design</div>;
  };
  ```
