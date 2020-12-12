
* ### React
	* Declarative, efficient JS library for making front end interfaces.
	* Uses `components` which are composed together to form complex UIs.
    * Components take `props` and maintain `state` as the source of truth, also returning views to display in the `render` method.
    * `setState` is used to set state of component, defined in constructor.
    * NOTE - any change in state or props will trigger re-render of component. Can modify behaviour by editing `shouldComponentUpdate` which checks whether component output should change or not. However, not recommended.

* ## React lifecycle
    * mounting component (inserting in the DOM tree), unmounting component, updating component.
    * `render()` - prepares the UI of the app, should have no side effects, pure and returns Arrays of React elements/ DOM nodes or Portals.
    * `componentDidMount()` - invoked after component is mounted - initialization needing DOM nodes, fetching network requests etc.
    * `componentDidUpdate(prevProp, prevState, snapshot)` - invoked after updating occurs. operate on DOM after update of component, perform a side effect.
    * `componentWillUnmount()` - invoked before component is unmounted or destroyed. Do cleanup - destroy timers, clean subscriptions/

* Hooks

* Context
    