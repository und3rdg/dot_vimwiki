## Jest API
The Jest API focusses more on the ability to define tests, make assertions, and create mocks.

    describe   : defines a test suite.
    it         : defines a test.
    beforeEach : defines an entry hook before running each test.
    expect     : makes an assertion.
    jest.fn()  : creates a mock function.

### Several methods are available for assertions.

    toEqual     : checks if two objects have the same value.
    toBe        : checks if two objects have the same value and type.
    toBeDefined : checks if the object is defined.
    toContain   : checks if an item is present in a list.
    toBeCalled  : checks if a mock function is called.

### There are useful methods on the mock.

    mockImplementation : provides an implementation for the mock function.
    mockReturnValue    : returns a value when the mock function is called.

## Enzyme API
Enzyme API focusses on rendering the react component and retrieving specific nodes from the rendered tree. There are three ways to render a component.

    shallow : renders only the component under test. Dependent components are not rendered.
    render  : renders the component as static HTML.
    mount   : mounts the full component in JSDOM.

### There are several methods to retrieve nodes from the rendered component.

    find      : accepts a selector and retrieves nodes that match the selector.
    findWhere : retrieve nodes selected by the predicate.
    some      : returns true if there is at-least one node matching the selector.
    someWhere : returns true if there is at-least one node selected by the predicate.
    first     : returns the first node of a set.
    at        : returns the nth node of a set.
    html      : gets the HTML of the node.
    text      : gets the text representation of the node.

### There are more methods to interact with the component and retrieve the component state.

    simulate     : simulates an event.
    setProps     : sets the props.
    setState     : sets the state.
    setContext   : sets the context.
    prop(key)    : retrieves prop value corresponding to the provided key.
    state(key)   : retrieves state corresponding to the provided key.
    context(key) : retrieves context value corresponding to the provided key.
