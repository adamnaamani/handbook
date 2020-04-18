# Javascript

## Table of Contents
1. [Linting](#linting)
1. [Debugger](#debugger)
1. [Radix](#radix)
1. [Booleans](#booleans)

## Linting
* ESLint
```bash
./node_modules/.bin/eslint --ext .js,.jsx ‘folder/‘
```

## Debugger
```javascript
debugger
```

## Radix
> The base in mathematical numeral systems.

Using a 10 radix means the number is parsed with a base 10 and thus turns the number into the integer you're expecting.
```javascript
function roughScale(x, base) {
  const parsed = parseInt(x, base)
  if (isNaN(parsed)) { return 0 }
  return parsed * 100
}

console.log(roughScale('100', 10))
// expected output: 10000
```

## Booleans
* True/False  
  > Returns the boolean true/false association of a value.
  ```javascript
  !!
  ```
