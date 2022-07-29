---
preload: false
---

<style>
.click_section_10.slidev-vclick-prior {
  display: none;
}
.click_section_10.slidev-vclick-current {
  display: block;
}
</style>

## Union Types

<v-clicks>
<div class="click_section_10">

```ts
function printId(id: number | string) {
  console.log("Your ID is: " + id);
}
// OK
printId(101);
// OK
printId("202");
// Error
printId({ myID: 22342 });
```

</div>

<div class="click_section_10">

```ts
type Circle = {
  cx: number;
  cy: number;
  r: number;
}

type Square = {
  cx: number;
  cy: number;
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
</v-clicks>
