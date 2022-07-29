---
preload: false
---

<style>
.click_section_05.slidev-vclick-prior {
  display: none;
}
.click_section_05.slidev-vclick-current {
  display: block;
}
</style>

## Basic Types

<v-clicks>

<div class="click_section_05">

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

<div class="click_section_05">

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

<div class="click_section_05">

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

<div class="click_section_05">

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

<div class="click_section_05">

### Array

```ts
const list: number[] = [1, 2, 3];
const extendedList: Array<number> = [...list, 4];
```
</div>

<div class="click_section_05">

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

<div class="click_section_05">

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

<div class="click_section_05">

### Enum Alternatives

```ts
enum StatusCode {
  ErrorCode = 404,
  SuccessCodeUpdated = 200
}


const STATUS_CODE = {
  ErrorCode: 404,
  SuccessCode: 200
} as const;


type StatusCodeObj = typeof STATUS_CODE[keyof typeof STATUS_CODE];

const statusResponse: StatusCode = StatusCode.ErrorCode;
const statusResponseObj: StatusCodeObj  = STATUS_CODE.ErrorCode;

function logger(code: StatusCodeObj) {}

logger(200); // <= ok
logger(300);// Error: Argument of type '300' is not assignable to parameter of type 'StatusCodeObj'.
```


</div>

</v-clicks>
