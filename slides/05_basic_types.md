---
preload: false
---

<style>
.slidev-vclick-prior {
  display: none;
}
.slidev-vclick-current {
  display: block;
}
</style>

## Basic Types

<v-clicks>

<div>

### Boolean

```ts
function getFlag() {
  return Math.random() > 0.5;
}

const isDone: boolean = false;
const isPerfect = getFlag();

let numeric = 5;

// TypeError: Type 'boolean' is not assignable to type 'number'.
numeric = getFlag();
```
</div>

<div>

### Number

```ts
let decimal: number = 6;
const hex: number = 0xf00d;
const binary: number = 0b1010;
const octal: number = 0o744;


//  ECMAScript 2020 only
let bar: bigint = 100n; // a BigInt literal
let foo: bigint = BigInt(100); // the BigInt function

foo = decimal; // error: Type 'bigint' is not assignable to type 'number'.
decimal = foo; // error: Type 'number' is not assignable to type 'bigint'.

```
</div>

<div>

### String

```ts
const name: string = "Bob";
const fullname: string = `${name} Johnson`;

// Literal Types
let x = "hello" as const;
let x2: "hello" = "hello";
let x3 = "hello";

x = 'other'; // error: Type '"other"' is not assignable to type '"hello"'.
x2 = 'other'; // error: Type '"other"' is not assignable to type '"hello"'.
x3 = 'other'; // ok

```
</div>

<div>

### Symbol

```ts
const sym1 = Symbol();
const sym2 = Symbol("key"); // optional string key

const sym3 = Symbol("key");
const sym4 = Symbol("key");
sym3 === sym4; // false, symbols are unique

const a = { [Symbol('test')]: 1 }
console.log(Object.keys(a)) // <= []

```
</div>

<div>

### Array

```ts
const list: number[] = [1, 2, 3];
const extendedList: Array<number> = [...list, 4];
```
</div>

<div>

### Tuple

```ts
let someStr: string;
const list: [string, number] = ['str', 4];

const key: string = list[0];
const value: number = list[1];

// TypeError: Type 'number' is not assignable to type 'string'.
someStr = list[1];

```
</div>

<div>

### Enum

```ts
enum Color {
  Red,
  Green,
  Blue,
}

enum CustomColor {
  Red = 1,
  Green,
  Blue,
}

enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}

enum BooleanLikeHeterogeneousEnum {
  No = 0,
  Yes = "YES",
}
```
</div>

<div>

### Null & Undefined

```ts
const a: string | null = null;
const b: undefined = undefined;

// Non-null Assertion Operator (Postfix!)
// No error reported
a!.toUpperCase();
```


</div>

</v-clicks>
