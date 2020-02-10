# Jest

## Table of Contents
1. [Enzyme](#enzyme)
2. [Describe](#describe)

## Enzyme
* Shallow Rendering

Shallow rendering is useful to constrain yourself to testing a component as a unit, and to ensure that your tests aren't indirectly asserting on behavior of child components.

## Describe
```javascript
describe()
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