## Functions

```ts
type MyFunc = (message: string) => boolean;

const myFunc1: MyFunc = (message) => message.length > 5; 

function myFunc(message: string): boolean {
  return message.length > 5;
}

type MyObj = {
  action: (message: string) => boolean;
  action2(message: string): void;
}

const myObj: MyObj = {
  action: str => str.length > 5,
  action2: () => {}
}
```
