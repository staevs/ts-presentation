---
preload: false
---

<style>
.click_section_11.slidev-vclick-prior {
  display: none;
}
.click_section_11.slidev-vclick-current {
  display: block;
}
</style>

## Intersection Types

<v-clicks>
<div class="click_section_11">

```ts
type CenterCoords = {
  cx: number;
  cy: number;
}

type Circle = CenterCoords & {
  r: number;
}

type Square = CenterCoords & {
  edge: number;
}

type Shape = Circle | Square | null;

function logger(shape: Shape) {
  console.log(shape.cx); // Error: Object is possibly 'null'.
  if (shape) {
    console.log(shape.cx) // <= OK
    console.log(shape.edge) // Error: Property 'edge' does not exist on type 'Circle | Square'.
    
    console.log((shape as Square).edge) // <= OK
  }
}
```

</div>

<div class="click_section_11">

```ts
type WeirdType = string & number;

const foo: WeirdType = '123'; // Error: Type 'string' is not assignable to type 'never'.

type CenterCoords = {
  cx: number;
  cy: number;
}

type Circle = CenterCoords & {
  cx: string;
  r: number;
}

const circle: Circle = {
  cx: '12px', // Error: Type 'string' is not assignable to type 'never'.
  cy: 12,
  r: 100
}

```

</div>

<div class="click_section_11">

```ts
type CenterCoords = {
  cx: number;
  cy: number;
}

type Circle = Omit<CenterCoords, 'cx'> & {
  cx: string;
  r: number;
}

const circle: Circle = {
  cx: '12px', // <= OK
  cy: 12,
  r: 100
}

const circle2: Circle = {
  cx: 12, // <= Error: Type 'number' is not assignable to type 'string'.
  cy: 12,
  r: 100
}
```

</div>

</v-clicks>
