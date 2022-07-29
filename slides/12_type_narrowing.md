---
preload: false
---

<style>
.click_section_12.slidev-vclick-prior {
  display: none;
}
.click_section_12.slidev-vclick-current {
  display: block;
}

.click_section_12 .slidev-code{ 
  max-height: 40vh;
  overflow: auto;
}
</style>

## Type Narrowing

<v-clicks>
<div class="click_section_12">

```ts
type CombinedType = string | number | boolean | null;

function logger(shape: CombinedType){
  if (shape === true || shape === false) {
    console.log(shape.toUpperCase()) // Error: Property 'toUpperCase' does not exist on type 'boolean'.
  }

  switch (typeof shape) {
    case 'string':
      console.log(shape.toUpperCase()); // <= Ok
      return;
    case 'number': {
      console.log(shape + 5); // <= Ok
      return;
    }
  }
}
```

</div>

<div class="click_section_12">

```ts
type CenterCoords = {
  cx: number;
  cy: number;
}
type Circle = CenterCoords & {
  type: 'Circle'
  r: number;
}

type Square = CenterCoords & {
  type: 'Square'
  edge: number;
}

type Shape = Circle | Square;

function isCircle(shape: Shape): shape is Circle {
  return shape.type === 'Circle';
}

function logger(shapes: Shape[]){
  shapes.forEach(shape => {
    if (shape.type === 'Square') {
      console.log(`Square with edge ${shape.edge}`)
    } else {
      console.log(`Circle with edge ${shape.r}`)
    }

    if (isCircle(shape)) {
      console.log(`Circle with edge ${shape.r}`)
    }
  })

  const circles = shapes.filter(shape => shape.type === 'Circle');
  circles.forEach(shape => {
    console.log(`Center is ${shape.cx}:${shape.cy}`) // <= Ok
    console.log(`Circle with edge ${shape.r}`) // Error: Property 'r' does not exist on type 'Square'.
  })

  const circles2 = shapes.filter(isCircle);
  circles2.forEach(shape => {
    console.log(`Circle with edge ${shape.r}`)
  })
}

```

</div>

</v-clicks>
