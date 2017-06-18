# rfc-js-destructuring-creation
A proposal for JS destructuring creation.

Given:

```js
const someObject = { a: 1, b: 2, other: 0 }
const otherObject = { c: 3, d: { nested: 4 } }
```

then

```js
const newObject = {
  { a, b } = someObject,
  { c: newC,
    d: { nested }
  } = otherObject
}
```

results in `newObject` being:

```js
{
  a: 1,
  b: 2,
  newC: 3,
  nested: 4
}
```

instead of having to first elevate things to variables then redundantly re-construct:

```js
const { a, b } = someObject
const {
  c: newC,
  d: { nested }
} = otherObject

const newObject = {
  a, b, newC, nested
}
```
