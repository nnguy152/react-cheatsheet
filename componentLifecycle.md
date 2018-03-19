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
  #### 1 - _Mounting_ : What happens when component created. Was an initial state set?
    _constructor()_: Called before react component is mounted. Place to initialize state and bind event handlers to the class instance. Otherwise, not needed. Can be used to initialize state based on props like:
      ```
      constructor(props) {
        super(props);
        this.state = {
          color: props.initialColor
        };
      }
      ```
      BUT state won't be updated when props is updated. Better to lift state up to the next common parent container. If done, use _componentWillRecieveProps(nextProps)_ to keep state up-to-date.
    _componentWillMount()_: Invoked just before mounting occurs; Called before render() so this.setState won't trigger extra rendering. 
    _render()_: Examines this.props & this.state to return:
      - React element created via JSX (<div></div> OR <Class />).
      -String/Numbers rendered as text nodes in the DOM.
      - Portals created via ReactDOM.createPortal.
      - null aka nothing.
      - Booleans that rendered nothing but return test.
    Render is 'pure' aka does not modify component state and retursn the same result each time it is invoked. 
    _componentDidMount()_: Invoked right after component mounted. If data needs to be loaded from remote endpoint, use this to instantiate network request. Calling this.setState will trigger extra rendering before browser updates screen (meaning render() will occur twice but user will not see the intermediate state).
    _componentWillUnmount()_: For when a component is being removed from the DOM. 

  #### 2 - _Updating_: Caused by change to props or state and re-rendering a component.
    _componentWillRecieveProps()_: Used when 'forking' props by using this in state to keep state up-to-date. Is invoked before mounted component recieves new props. If state needs to update in response to prop changes, compare this.props and nextProps and perform state transitions via this.setState.
    _shouldComponentUpdate()_: Lets React know if component output is not affected by current chang in props/state. Default behavior is to re-rnder on every state change. If false, componentWillUpdate() & componentDidUpdate() will not be invoked.
    _componentWillUpdate()_: Invoked before rendering new props or state being recieved. Not called for the initial render. Used as a way to perform prep before an update occurs. Can't call this.setState here or anything that will update to a component before componentWillUpdate() occurs.
    render()
    _componentDidUpdate()_: Invoked right after updating occurs. Not called for initial render. Used to do network requests as long as you compare current props to previous. Should not be invoked if shouldComponentUpdate returns false.