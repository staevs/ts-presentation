---
preload: false
---

## Interfaces

### An interface declaration is another way to name an object type:

```ts
interface IPoint {
  x: number;
  y: number;
}

interface IPoint {
  z: number;
}

// Declarations merged
const coordinate2: IPoint = { x: 4, y: 5, z: 6 }

type Point = {
  x: number;
  y: number;
};

// error: Duplicate identifier 'Point'.
type Point {
  z: number;
}
```
