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
## Advanced

### Operators
Ternary operator
```tsx
isMember ? '$2.00' : '$10.00'
// Expected output: '$2.00' if isMember == true
```
Nullish coalescing operator
```tsx
user?.verified ?? default_string
// Expected output: "default string" if user is not defined
```

### Unions
Using `&`
```tsx
type Developper = {
  name: string
}

type FrontEndDev = Developper & {
  frontEndFramework: string
}

type BackEndDev = Developper & {
  backEndFramework: string
}

type FullStackDev = FrontEndDev & BackEndDev
```

Using `|`
```tsx
type StudentDev = FrontEndDev | BackEndDev | FullStackDev
```

Using `interface`
```tsx
interface IDevelopper {
  name: string
}
interface IFrontEndDev extends IDevelopper {
  frontEndFramework: string
}
interface IBackEndDev extends IDevelopper {
  backEndFramework: string
}
interface IFullStackDev extends IBackEndDev, IFrontEndDev {}
```

### Unknown props
```tsx
type Student = {
  id: number
  note: string
}
interface ClassRoom {
  [key: string]: Student
}
const classroom: ClassRoom = {
  jack: {'id': 342, 'note': '20/20'},
  sylvia: {'id': 342, 'note': '14/20'},
  robert: {'id': 232, 'note': '6/20'},
}
classroom.jack.note
```

### Overload
```tsx
type InputDate = string | number | Date

function printBirthDay(year: number, month: number, day: number): string
function printBirthDay(year: number, month: number): string
function printBirthDay(year: number): string
function printBirthDay(inputDate: Date): Date
function printBirthDay(inputDate: string): string
function printBirthDay(inputDate: InputDate, m?: number, d?: number) {
  if (inputDate instanceof Date) {
    return inputDate
  } else if (typeof inputDate === 'string') {
    return new Date(inputDate).toLocaleDateString()
  } else if (d !== undefined && m !== undefined) {
    return new Date(inputDate, m, d).toLocaleDateString()
  } else if (m !== undefined) {
    return new Date(inputDate, m, 1).toLocaleDateString()
  } else if (typeof inputDate === 'number') {
    return new Date(inputDate, 0, 1).toLocaleDateString()
  } else {
    return 'Non définie'
  }
}

displayText(`${printBirthDay('October 13, 2014')}`)
displayText(`${printBirthDay(new Date(2014, 9, 13)).toLocaleDateString()}`)
displayText(`${printBirthDay(2014, 9, 13)}`)
displayText(`${printBirthDay(2014, 9)}`)
displayText(`${printBirthDay(2014)}`)
```
