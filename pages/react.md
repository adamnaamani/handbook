# React

## Table of Contents
1. [Lifecycle Methods](#lifecycle-methods)
1. [Functional Components](#functional-components)
1. [Hooks](#hooks)
1. [Fragments](#fragments)

## Lifecycle Methods
* `componentDidMount`
* `componentDidUpdate`
* `render`

## Functional Components
Prefer pure functions over class components.
```javascript
const Listing = () => {
  return (
    <div />
  )
}

export default Listing
```

## Hooks
* `useState`   
  ```javascript
  const [item, setItem] = useState()
  ```
* `useEffect`   
  ```javascript
  useEffect(() => {
    onMount()
  }, [])
  ```

## Fragments
Prevent additional, unnecessary nodes being added to the DOM.
> Use shorthand `<></>` instead of `<Fragment></Fragment>`
```javascript
const Listing = () => {
  return (
    <>
      <Details />
      <Neighborhood />
    </>
  )
}
```
