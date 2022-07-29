---
preload: false
---

<style>
.click_section_08.slidev-vclick-prior {
  display: none;
}
.click_section_08.slidev-vclick-current {
  display: block;
}
</style>

## Special Types

<v-clicks>
<div class="click_section_08">

### Any

```ts
let foo: any;

foo = 4; // <= OK
foo = 'str'; // <= OK
foo = {}; // <= OK

foo.toUpperCase(); // <= OK
```

</div>

<div class="click_section_08">

### Unknown

```ts
let foo: unknown;

foo = 4; // <= OK
foo = 'str'; // <= OK
foo = {}; // <= OK

foo.toUpperCase(); // Error: Object is of type 'unknown'.

if (typeof foo === 'string') {
  foo.toUpperCase(); // <= OK
}
```

</div>

<div class="click_section_08">

### Void

```ts
let foo: void;

foo = 4; // <= Error
foo = undefined // <= Ok


function amILucky(): void {
  const num = Math.random(); 
  if (num === 1) {
    return; // <= OK
  }
  return Math.random() > 0.5; // Error: Type 'boolean' is not assignable to type 'void'.
}

```

</div>

<div class="click_section_08">

### Never

```ts
let foo: never;

foo = 4; // <= Error: Type 'number' is not assignable to type 'never'.
foo = 'str'; // <= Error: Type 'string' is not assignable to type 'never'.
foo = {}; // <= Error: Type '{}' is not assignable to type 'never'.

// Return type is "never"
function amILucky(): never {
  if (Math.random() > 0.5) {
    return; // Error: Type 'undefined' is not assignable to type 'never'.
  }
  throw new Error('Something went wrong!')
}

// Never type should be declared 
// otherwise return type would be "void"
function error(message: string) {
  throw new Error(message);
}

```

</div>
</v-clicks>
