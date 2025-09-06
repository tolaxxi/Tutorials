# typeScript Full Course

javascript with super powers

## installing typescript

1. install as dev dependency

```bash
npm i typescript -D
```

2. initialize the config file

```bash
npx tsc --init
```

P.s you can use vite

## Recommendation

If you’re starting fresh → use Vite’s TypeScript template.
It’s cleaner, no extra setup, and avoids mistakes in tsconfig.json.

If you’re migrating an existing JS app → install TypeScript manually.

## Annotations

used to specify the data type of a variable ,parameter, function return value and other type of values . it helps developer catch errors in early stage of development by allowing them to specify what types of values can be assigned to a given variable

_demonstration_

```ts
const myName: string = 'tolani';
```

## type inference

is a feature in typescript that allows the compiler to detect the type of value assigned to a variable

## Types

- string

- number

- boolean

- any - type script has a special any type that can be used to represent any type <span style ="color:red "> _use with caution_</span>

- Void - represent the absent of any value it is often used as the return type of functions that do not return any value

- Never - used to indicate that a function would not return anything or that a variable can never have a value . it can help catch errors at compile time instead of run time

  <u>when to use "never" type</u>

  - a function that always throws an error .
  - a function that has an infinite loop.
  - a variable that can never have a value

- Array - are type of objects that can store multiply values of the same data type. arrays in typescript are typed which means you can specify the type of values an array can hold

  <u>there are two ways of creating an a array in typescript </u>

  - using the square bracket notation "[ ]" to indicate an array of a specific type

  - using the generic "Array< type >" notation to indicate an array of a specific type (this is the old way)

  _demonstration_

  ```ts
  const num: number[] = [1, 2, 3, 4];
  const nums: Array<number> = [1, 2, 3, 4]; \\ older method
  ```

  Nested Arrays: is an array that contains other arrays as it elements

  _demonstration_

  ```ts
  const singleDi: number[] = [1, 2, 3, 4];
  const doubleDi: number[][] = [[1, 2, 3]];
  const tripleDi: number[][][] = [[[1, 2, 3]]];
  ```

- Object - an object in typescript is a structured data type that represents a collection of properties each with a key and associated value
  _demonstration_

  ```ts
  const person: { name: string; age: number; isActive: boolean } = {
    name: 'john',
    age: 30,
    isActive: true,
  };

  <!-- constructor function -->

  function printUser(name: string, age: number): { name: string; age: number } {
  return { name, age };
  }

  ```

## function parameters annotation

used to specify the expected type that the function parameter should take

_demonstration_

```ts
function myFunc(num: number) {
  // regular function
}

const myFunc2 = (num: number) => {
  // arrow function
};
```

## Default parameter

used to set a parameter default value if one is not provided

_demonstration_

```ts
function myFunc(num: number = 'default') {
  // regular function
}
```

## return Annotations

used to set what type a function should return

```ts
function double(num: number): number {
  return num * 2; // has to return a number
}

const multiply = (num: number): number => {
  return num * 2;
};

function printUser(name: string, age: number): { name: string; age: number } {
  return { name, age };
}
```

## Type Aliases

it is a way to create a new name for an existing type it allows you to define a custom type that refers to another type and give it a more meaningful or descriptive name

_demonstration_

```ts
type myType = string;

type User = {
  name: string;
  age: number;
  isActive: boolean;
};

const printUserInfo = (user: User) => {
  return `
  Name : ${user.name}
  age: ${user.age}
  online: ${user.isActive}`;
};

const res = printUserInfo({ name: 'alex', age: 10, isActive: true });

console.log(res);
```

## optional properties

you can make a property optional in an object type by just adding a question mark after the property name

_demonstration_

```ts
type User = {
  name: string;
  age?: number;
  isActive: boolean;
};

const printUserInfo = (user: User) => {
  return `
  Name : ${user.name}
  age: ${user.age}
  online: ${user.isActive}`;
};
// you can chose to provide the age value
const res = printUserInfo({ name: 'alex', isActive: true });

console.log(res);
```

## readonly keyword

is essential a keyword that when add to the front of a key it makes it readonly (you cant edit it)
_demonstration_

```ts
type User = {
  name: string;
  age?: number;
  readonly location: string;
};

const user: User = {
  name: 'huXn',
  location: 'china',
};

user.location = 'Usa'; //can't edit cause it is readonly

console.log(user);
```

## intersection type

an intersection type is a way to combine multiple type into a single type that includes all the properties and methods of each constituent type it is denoted by the "&" symbol

_demonstration_

```ts
type UserInfo = {
  first: string;
  last: string;
  age: number;
};

type AccountDetails = {
  email: string;
  password: string;
};

type User = UserInfo & AccountDetails;

const person: User = {
  first: 'john',
  last: 'doe',
  age: 21,
  email: 'johndoe@gmail.com',
  password: 'password12',
};

console.log(person);
```

## union Type

are used to declare a type that can have one or several possible type
its syntax is "|" symbol

_demonstration_

```ts
let myVar: number | string; // for variables

// for function parameter

function (params:string[]|string){
  // function body
}

// for types

type UserInfo = {
  name: string;
  password: number | string;
};
type AccountInfo = {
  email: string;
  otp: string;
  password: string;
};

let login: UserInfo | AccountInfo = {
  name: 'john Doe',
  password: '123@',
};

// for arrays
const items: (number | string)[] = [1, 2, 'w'];

```

## Literal types

allows you to specify a value that can only be one specific literal value.this means that a variable with a literal type can only have one specific value and no other

_demonstration_

```ts
// string literal type

let color: 'red' | 'blue' | 'green' | 'yellow';

color = 'pink'; // cant assign pink cause it is not part of the type
color = 'yellow';

//boolean literal type

let isTrue: true | false;

// etc
```

## Tuples

is a type that represent an array with a fixed number of element, where each elements can have a different type

```ts
let myTuples: [string, number] = ['hello', 2];
console.log(myTuples[0]); //hello
console.log(myTuples[1]); // 2

// destruction  a tuple

let myTuple: [string, number] = ['hello', 2];

let [first, second] = myTuple;
console.log(first); //hello
console.log(second); // 2
```

## Enums

is a way to define a set of named constants . enums allows you to define a collection of related values that can be used interchangeable in your code

_demonstration_

```ts
enum weatherCondition {
  sunny,
  cloudy,
  rainy,
}

console.log(weatherCondition.sunny); // output is 0 cause no value was assigned

// assigning values

enum weatherCondition {
  sunny = 'sunny',
  cloudy = 'cloudy',
  rainy = 'rainy',
}

console.log(weatherCondition.sunny); // sunny
```

## class properties annotation

you can annotate class properties with a type this allows you to define the data type of a property and ensure it is always consistent

_demonstration_

```ts
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

const john = new Person('john', 20);

console.log(john);
```

## Interface

is a way to define a contract for the shape of an object .it specifies the properties and their types that an object must have, they are powerful tool for enforcing a certain structure in your code . they can also be used to define the shape of a function and classes

_demonstration_

```ts
// interface definition

interface Movie {
  readonly name: string;
  ratings: number;
  genre?: string;
}
// using the interface with an object

const movieOne: Movie = {
  name: 'Star Wars',
  ratings: 2,
  genre: 'action',
};

// interface for function

interface MathOperations {
  (x: number, y: numb er): number;
}
// using the interface for functions

const add: MathOperations = (a, b) => a + b;

console.log(add(2, 3));
```

## Generics

in typescript ,generics allow you to create reusable components that can work with a variety of types.they make it possible for you to define function,classes and interfaces with different data types without having to duplicate them

_demonstration_

```ts
function printTypes<T>(item: T, defaultValue: T): [T, T] {
  return [item, defaultValue];
}

const str = printTypes<string>('hello', 'world'); // you can set any data type instead of having to create the function from scratch

console.log(str);

// using generic with your custom type
function identityOne<T>(val: T): T {
  return val;
}

interface User {
  name: string;
  age: number;
}

const userOne = identityOne<User>({ name: 'tolani', age: 10 });

console.log(userOne);
```

## Type Narrowing

type narrowing is the process of refining a variables type within a conditional block of code . this allows you to write more precise and type safe code

_typescript provides several ways for narrowing types_

- Type guards
  A type guard is any expression that checks the type of a variable and lets TypeScript know more about it.
  Once TypeScript sees the check, it narrows the type inside that code block.

```ts
//  using typeof

type myType = string | number;

function example(value: myType): void {
  if (typeof value === 'string') {
    console.log(value.toUpperCase());
  } else {
    console.log(value.toFixed());
  }
}
```

- the instanceof operator - is another instance of type guard that allows you to check if an object is an instance of a particular class or constructor function

```ts
class Dog {
  bark(): void {
    console.log('woff woff');
  }
}

class Cat {
  meow(): void {
    console.log('woff woff');
  }
}

function animalSound(animal: Dog | Cat): void {
  if (animal instanceof Dog) {
    animal.bark();
  } else {
    animal.meow();
  }
}

const myDog = new Dog();
const myCat = new Cat();

animalSound(myDog); //woff woff
```

- intersection types

```ts
type Employee = {
  id: number;
  name: string;
};
type Manager = {
  department: string;
  role: string;
};

type ManagerWithEmployeeInfo = Employee & Manager;

const manager: ManagerWithEmployeeInfo = {
  id: 123,
  name: 'john doe',
  department: 'engineering',
  role: 'team lead',
};
```
