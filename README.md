# typescript-cheatsheet

## Init

Make sur to have Node installed

https://www.typescriptlang.org 

Install Typescript globally   
`npm install -g typescript`

Compile ts code  
`tsc sript.ts`

Create `tsconfig.json` file   
`tsc --init`

Run auto compile with `watch`   
`tsc -w`

## Basics

### Basic types

Possible types are : `number, boolean, string, object, any, undefined, Function`

```tsx
// Variable
const age : number = 32

// Types in function
function foo(arg : string) {
	//...
}
```
### Array

```tsx
let ages: number[]  // or let ages: Array<number>
ages = [23, 54, 13, 65]
```

### QuerySelector

```tsx
// Single
const div = document.querySelector('div')  // HTMLDivElement | null
const span = document.querySelector('span')  // HTMLSpanElement | null

const form = document.querySelector('form')  // HTMLFormElement | null
form?.appendChild(cb)

// Multiple
const inputs = document.querySelectorAll('input')  //NodeListOf<HTMLInputElement>
```

### Custom type
```tsx
type Person = {
  name: string
  age: number
  friend: Person | undefined
}
type Gender = 'Mr' | 'Mrs' | 'Ms'

```

### Tuples
```tsx
const pair: [number, number] = [23, 54]

```

### Enums
```tsx
enum Protocol {
  HTTP = 'http',
  HTTPS = 'https',
  FTP = 'ftp',
}

```

### Destructuring
```tsx
type Connexion = [string, Protocol, string]
const gmail: Connexion = ['Gmail', Protocol.HTTPS, 'gmail.com']
let [, gmailProtocol] = gmail

```

### Functions
```tsx
function basicFunction = (value: Number): number {
  return value + 2
}

type SomeBasicFunction = {
  description: string
  (arg: number): number
}

function otherFn(fn: SomeBasicFunction, base: number): number {
  return fn(base)
}
```

