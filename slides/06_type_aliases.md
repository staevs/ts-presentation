---
preload: false
---

## Type Aliases

### A type alias is exactly that - a name for any type

```ts {all|6-9,13|all}
type Point = {
  x: number;
  y: number;
};

/** error: 
 * Type '{ x: number; y: number; z: number; }' is not assignable to type 'Point'.
 * Object literal may only specify known properties, and 'z' does not exist in type 'Point'.
 * **/
let coordinate: Point = {
  x: 3,
  y: 4,
  z: 5
}

const coordinate2 = {
  x: 3,
  y: 4,
  z: 5
}

coordinate = coordinate2; // <= ok

```
