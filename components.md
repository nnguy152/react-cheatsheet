# Components

React is composed of component-based separation of concerns. 
Components are functional elements that take in data to produce a dynamic UI using JSX, 
a language that uses JS functions to return HTML elements.

### First
  - Focused
  - Independent
  - Reusable
  - Small
  - Testable

There are two types of comoenents:
  - Presentational: Functional components that render data (does not have state) and can accept props.

  ```
  const Welcome = () => {
    return (
      <h1>Hello world</h1>
    )
  }
  ```

  - Container: Class components that render presentational components and pass them data via props (has state, which allows components to be reusable and encapsulated). Usually has a constructor to assign state.

  ```
  class Welcome extends Component {
    render() {
      return <h1>Hello, {this.props.name}</h1>;
    }
  }
  ```

---


