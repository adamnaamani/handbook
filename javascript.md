# Javascript

## Table of Contents

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