# Component Lifecycle

Lifcycle methods allow actions to happen in a specific order during the rendering process and control application based on the state of the UI.

Used for:
  - Making asynchronous requests
  - Binding event listeners to components
  - Animating components (once rendered)
  - Optimizing for performance (shouldComponentUpdate)

  ex: 
  - _componentWillUnmount_ is called before a component is removed from the DOM.
  - _componentDidMount_ is called after a comonent is rendered to the DOM.

### Two Types of Component Lifecycle Methods:
  #### - _Mounting_ : What happens when component created. Was an initial state set?
    - `constructor()`: Called before react component is mounted. Place to initialize state and bind event handlers to the class instance. Otherwise, not needed. Can be used to initialize state based on props like:
      ```
      constructor(props) {
        super(props);
        this.state = {
          color: props.initialColor
        };
      }
      ```
      BUT state won't be updated when props is updated. Better to lift state up to the next common parent container. If done, use `componentWillRecieveProps(nextProps)` to keep state up-to-date.
    - `componentWillMount()`: Invoked just before mounting occurs; Called before render() so this.setState won't trigger extra rendering. 
    - render()
    - `componentDidMount()`: Invoked right after component mounted. If data needs to be loaded from remote endpoint, use this to instantiate network request. Calling this.setState will trigger extra rendering before browser updates screen (meaning render() will occur twice but user will not see the intermediate state).
    - `componentWillUnmount()`: For when a component is being removed from the DOM. 

  #### - _Updating_: Caused by change to props or state and re-rendering a component.
    - `componentWillRecieveProps()`: Used when 'forking' props by using this in state to keep state up-to-date. Is invoked before mounted component recieves new props. If state needs to update in response to prop changes, compare this.props and nextProps and perform state transitions via this.setState.
    - shouldComponentUpdate()
    - componentWillUpdate()
    - render()
    - componentDidUpdate()