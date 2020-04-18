# Jest

## Table of Contents
1. [Commands](#commands)
1. [Enzyme](#enzyme)
    1. [shallow](#shallow)
    1. [mount](#mount)
1. [Methods](#methods)
    1. [describe](#describe)
    1. [it](#it)
1. [Expectations](#expectations)    
1. [Snapshots](#snapshots)
1. [Debugging](#debugging)
1. [Instances](#instances)
    1. [Stateful](#stateful)
    1. [Stateless](#stateless)
1. [Act](#act)

## Commands
```bash
npm test jest/
npm test --updateSnapshot
```

## Enzyme
* Shallow  
  > Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure that your tests aren't indirectly asserting on behavior of child components.
  ```javascript
  shallow(<Component />)
  ```
* Mount  
  > Renders a component to its extreme leaf nodes.  
  ```javascript
  mount(<Component />)
  ```

## Methods
* `describe`
  ```javascript
  describe('Component', () => {})
  ```
* `it`
  ```javascript
  it('should do something', () => {})
  ```

## Expectations
```javascript
expect(component.find('Node').exists()).toBeTruthy()
```

## Snapshots
```javascript
test('Should match snapshot', () => {
  const component = <Listing {...props} />
  expect(component.debug()).toMatchSnapshot()
})
```
Updating snapshots:
```bash
npm test -- -u
```

## Debugging
To see what Enzyme's `shallow` is actually rendering, you can console log the result with `debug()`.  
```javascript
console.log(component.debug())
```
You can also insert a debugger in the test, open `chrome://inspect`, and install a Chrome Node extension.
```javascript
debugger
```

## Instances
`instance()` can only be used on class components, and returns `null` for stateless functional components.  
> Can only be called on a wrapper instance that is also the root instance. With React 16 and above, instance() returns null for stateless functional components.  
* Stateful
  ```javascript
  class Listing extends Component {
    render() {
      return (
        <div>Stateful</div>
      )
    }
  }

  it('should succeed', () => {
    const wrapper = shallow(<Listing />)
    const instance = wrapper.instance()

    expect(instance).to.be.instanceOf(Listing)
  })
  ```
* Stateless
  ```javascript
  const Listing = () => (
    <div>Stateless</div>
  )

  it('should succeed', () => {
    const wrapper = shallow(<Listing />)
    const instance = wrapper.instance()

    expect(instance).to.equal(null)
  })
  ```

## Act
When writing UI tests, tasks like rendering, user events, or data fetching can be considered as “units” of interaction with a user interface. React provides a helper called act() that makes sure all updates related to these “units” have been processed and applied to the DOM before you make any assertions.  
  ```javascript
  import { act } from 'react-dom/test-utils'

  act(() => {
    // render components
  })
  // make assertions
  ```
