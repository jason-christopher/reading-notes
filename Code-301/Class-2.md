# State and Props

## React lifecycle

1. Based off the diagram, what happens first, the ‘render’ or the ‘componentDidMount’?
   * render
2. What is the very first thing to happen in the lifecycle of React?
   * Mounting in the "render phase" starting with constructor.
3. Put the following things in the order that they happen: componentDidMount, render, constructor, componentWillUnmount, React Updates
   * constructor, render, React updates, componentDidMount, componentWillUnmount
4. What does componentDidMount do?
   * Used immediately after a component is mounted to load anything using a network request or to initialize the DOM.

## React State Vs Props

1. What types of things can you pass in the props?
   * Information unique to that component, but it should only be used for initial information.
2. What is the big difference between props and state?
   * Props are like the initial parameters while state can be updated from the initial props.
3. When do we re-render our application?
   * Every time the state changes or information is updated in the app.
4. What are some examples of things that we could store in state?
   * For a news website, the time since an article was posted or how many "likes" it has from social media interaction.
