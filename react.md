# REACT

A JavaScript library for building user interfaces

## installing react

```bash
  npm create vite@latest
```

## folder structure

1. node_modules/: contains all the module and packages your project need to run

2. public/: where we put all our assets files

3. src/:the heart of our project

4. src/assets : where we pt all our images

## components

- they are independent and reusable bits of code they are basically javascript functions that return html(jsx)

### how to create a component

<u>rules for creating a component</u>

1. your component file name must be in pascal case (ComponentName)
2. your component must return a jsx

```jsx
const ComponentName = () => {
  return <>// jsx code goes here</>;
};

export default ComponentName;

function ComponentName() {
  return <>// jsx code goes here</>;
}

export default ComponentName;
```

### consuming a component

```jsx
import ComponentName from './filePath';

const ParentComponent = () => {
  return (
    <>
      <ComponentName />
    </>
  );
};

export default ParentComponent;
```

## JSX

jsx allows us to write html in react

### writing JSX

```jsx
const ComponentName = () => {
  return (
    <>
      <h1> welcome to react jsx</h1>
      <p className="text"> paragraph content</p>
    </>
  );
};

export default ComponentName;
```

### rules for writing JSX

- always return a single root element
- you can't use `class` attribute instead you use `className`
- you can't use `for` attribute instead you use `htmlFor`
- Always close tag
- use `camelCase` for most things in jsx
- use curly braces for javascript expressions
- use self Closing tags for empty element

### Expressions in JSX

in jsx you can write javascript expression inside curly braces `{ }` JSX would execute the expression and return the result

```jsx
const ComponentName = () => {
const myName = "Tolani"

  return (
    <>
     <h1>{2+2}<h1/>
     <h1>welcome {myName}<h1/>
    </>
  );
};

export default ComponentName;
```

## Lists

in react you will render lists with soe type of loop. the javascript `map()` array method is generally the preferred method.

### demonstration

```jsx
const ComponentName = () => {
  const numbers = [1, 2, 3, 4];
  return <>{
    numbers.map((number,id)=>{
      <ul key={id+1}>
      <li>{number}<li/>
      <ul/>
    })
  }</li>;
};



const App = () => {
  const usersInfo = [
    {
      username: 'HuXn',
      email: 'test@gmail.com',
      location: 'USA',
    },
    {
      username: 'John',
      email: 'jd@gmail.com',
      location: 'Arab',
    },
    {
      username: 'Alex',
      email: 'alexmersion@gmail.com',
      location: 'India',
    },
  ];

  return (
    <>
      {usersInfo.map(({ username, email, location }) => {
        return (
          <ul>
            <li>{username}</li>
            <li>{email}</li>
            <li>{location}</li>
          </ul>
        );
      })}
    </>
  );
};
export default App;

```

p.s we should always provide a key

## Props

- props are arguments passed into react components

- props allows us to pass data from parent component to a child component

- props are passed to a components via html attributes

-props can receive any data tpe (number,boolean,object,array , )

### demonstration

```jsx
// passing props
import ComponentName from './ComponentName';

const App = () => {
  return <ComponentName name="userName" />;
};

// consuming Props
const ComponentName = (props) => {
  return (
    <>
      <h1>my name is {props.name}</h1>
    </>
  );
};

// consuming Props by destructuring
const ComponentName = ({ name }) => {
  return (
    <>
      <h1>my name is {name}</h1>
    </>
  );
};

// passing props using children

import ComponentName from './ComponentName';

const App = () => {
  return (
    <>
      <ComponentName>
        <h1>my name is huXn</h1>
        <p>i am 22 year old</p>
      </ComponentName>
    </>
  );
};

// consuming Props by using it's children P.s it can also be destructured as {children}
const ComponentName = (props) => {
  return <>{props.children}</>;
};
```

## Conditional Rendering

allows us to dynamically display different ui components or content based on specific conditions.this enables us to create more interactive and responsive user experience

### Methods of conditional rendering

- `if/else` statement
- ternary `?` operation
- logical AND operator `&&`

### demonstration

```jsx
//  using if/else statement
const ValidPassword = () => {
  return <h1>pass word is valid</h1>;
};
const InValidPassword = () => {
  return <h1>password is invalid</h1>;
};
const Password = ({ isValid }) => {
  if (isValid) {
    return <ValidPassword />;
  } else {
    return <InValidPassword />;
  }
};

const App = () => {
  return (
    <>
      <Password isValid={true} />
    </>
  );
};

// using ternary operation

const ValidPassword = () => {
  return <h1>pass word is valid</h1>;
};
const InValidPassword = () => {
  return <h1>password is invalid</h1>;
};
const Password = ({ isValid }) => {
  isValid ? <ValidPassword /> : <InValidPassword />;
};

const App = () => {
  return (
    <>
      <Password isValid={true} />
    </>
  );
};
// AND operator
const Cart = () => {
  const items = ['Bag', 'Laptop', 'Skin Care'];
  return (
    <>
      {items.length > 0 && <h1> you have {items.length} items in your Cart</h1>}

      <ul>
        <h2>Cart</h2>
        {items.map((item) => {
          return <li>{item}</li>;
        })}
      </ul>
    </>
  );
};
```

## Styling

there are a lot of ways to style components

- inline style
- external style sheet

```jsx
// using inline style p.s use  camelCase when using inline style, and also use a key value pair notation

const App = () => {
  return (
    <div>
      <Greeting style={{ color: 'red' }} />
    </div>
  );
};
export default App;
// external css
import "./stylesheet file path"
const App = () => {
  return (
    <div>
      <Greeting style={{ color: 'red' }} />
    </div>
  );
};
export default App;
```

## Adding Icons

there are a lot of icon library in react js but `react-icons` library is one of the most popular ones

### using React icons library

1. install it

```bash
npm install react-icons --save
```

2. usage

```jsx
import { FaBeer } from '@react-icons/all-files/fa/FaBeer';

const App = () => {
  return (
    <h3>
      Lets go for a <FaBeer />
    </h3>
  );
};
```

## Event Handling

```jsx
const Button = () => {
  function handleClick() {
    console.log('you clicked me');
  }
  return (
    <>
      <Button>Click me</Button>
    </>
  );
};
const App = () => {
  return <Button />;
};
```

## HOOKS AND STATES

### hooks

hooks are new addition in react 16.8 they let you use state and other react features without writing a class

### state

state is a way to store and manage data that can change over time and affects how a component renders -nwe define state using the `useState` hook , which allows you to set an initial value and provides a way to update that state

> any value type can be passed to a state

> data- the current value "data" can be any variable name

> setData - a function to change the value the convention is to add "set" + the variable name

```jsx
import { useState } from 'react';

const App = () => {
  const [data, setData] = useState(' initial value');

  return <div>App</div>;
};
export default App;

// example
import { useState } from 'react';

const App = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <h1> {count}</h1>
      <button
        onClick={() => {
          setCount((c) => c + 1);
        }}
      >
        +
      </button>
      <button
        onClick={() => {
          setCount((c) => c - 1);
        }}
      >
        -
      </button>
    </div>
  );
};
export default App;
// using use state with an array

import { useState } from 'react';

const App = () => {
  const [friends, setFriends] = useState(['alex', 'john']);
  function addF() {
    setFriends((f) =>[...f, 'car']);
  }
  return (
    <div>
      {friends.map((f) => {
        return (
          <ul>
            <li>{f}</li>
          </ul>
        );
      })}

      <button onClick={addF}>ADD</button>

    </div>
  );
};
export default App;
// using useState on an object

import { useState } from 'react';

const App = () => {
  const [movie, setMovie] = useState({ title: 'lion king', rating: 5 });
  function rateChange() {
    setMovie((m) => {
      return { ...m, rating: 4 };
    });
  }
  return (
    <div>
      <h1>movie name : {movie.title}</h1>
      <p>movie name : {movie.rating}</p>

      <button onClick={rateChange}>change rating</button>
    </div>
  );
};
export default App;

```

### Passing state and event handlers as props

```jsx
// passing them
import { useState } from 'react';
import ComponentOne from './components/ComponentOne.jsx';
import ComponentTwo from './components/ComponentTwo.jsx';

const App = () => {
  const [count, setCount] = useState(0);
  return (
    <div>
      <ComponentOne count={count} onclickHandler={/*f
        event handler goes here */ }/>
      <ComponentTwo />
    </div>
  );
};
export default App;
// consuming Them

const ComponentOne = ({ onclickHandler, count }) => {
  return (
    <div>
      <h1 onCLick={onclickHandler}>{count}</h1>
    </div>
  );
};
export default ComponentOne;

```

### lazy initializer (Passing Function as initial value To useState)

Normally, `useState(initialValue) `evaluates initialValue immediately on every render. But if you pass a function instead—like `useState(() => someExpensiveComputation())`

React only calls that function once, during the initial render, to set up the state.

- It’s useful when the initial value needs a heavy computation, or when you want to initialize from localStorage/sessionStorage without recalculating on every render.

```jsx
// example 1

import { useState } from 'react';

const App = () => {
  const [count, setCount] = useState(() => {
    const initialCount = 0;
    return initialCount;
  });
  return (
    <div>
      <h1>count :{count}</h1>
      <button
        onClick={() => {
          setCount((c) => {
            return c + 1;
          });
        }}
      >
        increment
      </button>
    </div>
  );
};
export default App;
// example 3 :using local storage

import { useEffect, useState } from 'react';

const ExampleThree = () => {
  const [name, setName] = useState(() => {
    const savedName = localStorage.getItem('name');
    return savedName ? JSON.parse(savedName) : '';
  });

  function handleChange(e) {
    setName(e.target.value);
  }

  useEffect(() => {
    localStorage.setItem('name', JSON.stringify(name));
  }, [name]);

  function clear() {
    setName('');
  }
  return (
    <div>
      <h1>name {name}</h1>
      <input type="text" value={name} onChange={handleChange} placeholder="enter your name" />

      <button onClick={clear}>Clear</button>
    </div>
  );
};
export default ExampleThree;


```

## React Portal

is a feature that allows you to render a child component into a Dom node that exists outside the hierarchy of the parent component. this can be useful in scenarios like modals,tooltips of dropdowns

### React Portal In Action

1. create the element you want to render your child into

```html
<body>
  <div id="root"></div>
  <div id="popupContent"></div>
  <script type="module" src="/src/main.jsx"></script>
</body>
```

2. import and use it like this in the child component

```jsx
import { createPortal } from 'react-dom';

const PopContent = ({ copied }) => {
  return createPortal(
    <section>
      {copied && <div style={{ position: 'absolute', bottom: '3rem', color: 'red' }}>copied to clipboard</div>}
    </section>,
    document.querySelector('#popupContent')
  );
};
export default PopContent;
```

## Advanced keys

keys basically lets you create unique ui,components or elements

```jsx
import { useState } from 'react';

const Switcher = () => {
  const [sw, setSw] = useState(false);
  const body = document.querySelector('body');
  return (
    <div>
      {sw ? body.classList.add('dark') : body.classList.remove('dark')}
      <input type="text" key={sw ? 'dark' : 'light'} />
      {/* basically lets you make this input field unique */}
      <button
        onClick={() => {
          setSw((s) => !s);
        }}
      >
        switch
      </button>
    </div>
  );
};
export default Switcher;
```

## useEffect Hook

allows you to perform sideEffects in your components . some examples of side effects are : fetching data directly updating the DOM etc

### syntax

```jsx
useEffect(
  () => {
    // code goes here
  },
  [
    /*optional*/
  ]
);

// 1. without an array -calls on every single render
// 2. you cant wrap your useEffect inside conditional Statement instead you  can use it inside
// 3. empty dependency array: run once on the initial render
// 4. with a specified state in the dependency array : runs any time the state changes
```

## Prop drilling

basically passing props from one component to another (manually) (not a good way to pass props)

## ContextAPI

it is a feature that allows you to manage and share state across your component tree without having to pass props down manually at every level
it is useful for scenarios where you need to share data or functions across many components especially when this components are deeply nested

_p.s: also not a good way to prop drill_

## Context api in action

1.  you import `createContext`

```jsx
import { createContext } from 'react';
```

2. then you create and instance of it

```jsx
export const MyContext = createContext();
```

3. then you pass your data

```jsx
function App() {
  const sharedData = 'Hello from Context!';
  return (
    <MyContext.Provider value={sharedData}>
      {/* Your components that need sharedData go here */}
      <ChildComponent />
    </MyContext.Provider>
  );
}
s;
```

4.consuming the data

```jsx
// first import the data ps you can pass more than one
import { sharedData, Data1 } from '../App.jsx';
const ComponentC = () => {
  return (
    <div>
      // then consume it like this
      <MyContext.Consumer>
        {(name) => (
          <MyContext.Consumer>
            // use a call back function to acess the passed value
            {(age) => {
              return (
                <h1>
                  {' '}
                  hello my name is {name} i am {age} years old
                </h1>
              );
            }}
          </MyContext.Consumer>
        )}
      </MyContext.Consumer>
    </div>
  );
};
export default ComponentC;
```

## useContext Hook

allows us to access the context values provided by a context object directly within a functional component P.s skipping all the bullshit call back hell

### useContext() in action

1. you import your context api in the component you want to pass the props from e.g the App component

```jsx
import { createContext } from 'react';
```

2. then you create an instance of your context and export it so you can access it in other component

```jsx
export const Data = createContext();
```

3. then you use it

```jsx
function App() {
  const name = 'tolani';
  // lets say we want to share the name
  return (
    <>
      <Data.Provider value={name}>
        // then you call the component you intend on using the name in it here
        <Profile />
      </Data.Provider>
    </>
  );
}
```

4. when using the context api it lets you ditch the original callback hell and lets you simplify things

```jsx
//  you first import it in the file you want to use the props that is being passed in

import { useContext } from 'react';
// import the data from the parent component
import { Data } from './App.jsx';

function Profile() {
  // initialize the context into a variable and specify the context location
  const userName = useContext(Data);

  return (
    // then use it
    <h1>my name is {userName}</h1>
  );
}
```

## useReducer Hook

it is similar to the useState but it is designed for more complex state object or state transitions that involves multiple sub values

### syntax

1. import first

```jsx
import { useReducer } from 'react';
```

2.using it

```jsx
const [state, dispatch] = useReducer[(reducer, initialState)];

// reducer - a function that describes how the state should change based on an action. it takes the current state and the action as parameter and returns a new state value

// initialState -  starting value for the state when a components first renders

// state - current state value which you can use inside your component

// dispatch - a function you call to send actions to the reducer  which then updates the state
```

## useRef Hook

provides a way to access and interact with the dom elements or to persist values across renders without causing a re render

1. import the useRef hook
2. save the useRef hook in a variable

```jsx
const myElement = useRef(null);
```

3.use the useRef hook

```jsx
function ComponentName() {
  const inputRef = useRef(null);

  function handleClick() {
    myElement.current.focus();
    myElement.current.value = 'HuXn';
  }
  return (
    <div>
      <input type="text" ref={myElement} />

      <button onClick={handleClick}> click and write HuXn</button>
    </div>
  );
}
```

## Custom Hooks

they are javascript functions that start with the prefix(e.g useFetch,ueForm) and can call other hooks within them they allow you to extract and reuse logic that involves state or sideEffects making your components more readable and maintainable

## demonstration

```jsx
//  create a separate file to house your function (custom hook)

// basic example
// useFetch.jsx

// creating custom hook
//  this hook basically lets use a fetch logic without having to create it every single time
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, []);

  return [data];
}
export default useFetch;
// using the custom hook
// first import yor custom hook

import useFetch from './useFetch';

const App = () => {
  // destructure it
  const [data] = useFetch('https://jsonplaceholder.typicode.com/posts');

  // you can go ahead an use it
  return (
    <div>
      {data &&
        data.map((p) => {
          return (
            <ul key={p.id}>
              <li>{p.title}</li>
            </ul>
          );
        })}
    </div>
  );
};
// export default App;
```

## useId hook

used to generate unique ids for components

```jsx
import { useId } from 'react';

const UniqueId = () => {
  const id = useId();
  return (
    <div>
      {/*  if you want to make the id unique for each element you prefix it  */}
      <label htmlFor={`${id}--email`}>email</label>
      <input type="email" id={`${id}--email`} />

      <label htmlFor={id}>passWord</label>
      <input type="password" id={id} />
    </div>
  );
};
export default UniqueId;
```

# react js with typescript

# types for props

```jsx
// passing props
import User from './components/User';

const App = () => {
  return (
    <div>
      <User name="alex" age={10} />
    </div>
  );
};
export default App;
// using props with types

// destructuring the props

// use an interface/a type  to set types of the props if you want to use destructured props
interface User {
  name: string;
  age: number;
}
// or

type User ={
  name: string;
  age: number;
}

const User = ({ name }: User) => {
  return (
    <div>
      <h2>name:{name}</h2>
    </div>
  );
};
export default User;

// using the props directly

const User = (props: { name: string; age: number }) => {
  return (
    <div>
      <h1>name:{props.name}</h1>
      <h1>age:{props.age}</h1>
    </div>
  );
};
// using types with props children

const App = () => {

  return (
    <div>
      <User>
        <p>hello</p>
      </User>
    </div>
  );
};
export default App;

// consuming the props

import type { ReactNode } from 'react';

interface childrenProps {
  children: ReactNode;
}

const User = ({ children }: childrenProps) => {
  return <div>{children}</div>;
};
export default User;


// using FC  to consume props (the old method)
import type { FC } from 'react';

interface userProps {
  name: string;
  age: number;
}

const User: FC<userProps> = ({ name, age }) => {
  return (
    <div>
      <h1>name:{name}</h1>
      <h1>age:{age}</h1>
    </div>
  );
};
export default User;

```

## reusable types

is basically creating reusable types and then exporting it to use in another file you can use whatever import/export method you like just make sure you provide the `type ` keyword

1. exporting it

```jsx
export type { typeName };
```

2. importing it

```jsx
import type { typeName } from 'file location';
```

## types for useState

basically to use a type for a useState , useState is basically a generic function

```tsx
const [name, setName] = useState<string>('tolani');
```

## types for useRef,forms & Event

### types for form

1. you define an interface for the form data

```tsx
interface FormData {
  name: string;
  age: number | null;
  password: string;
}
```

2. you then use it in a useState with the type of <Formdata>

```tsx
useState<FormData> ={
  name:""
  age:null
  password:""
}
```

### types for event(e.target)

to use events in reactc you need to specify the event type and where the event is coming from
note you have to import the event type

```tsx
import { ChangeEvent } from 'react';
function handleTyping(e: ChangeEvent<HTMLInputElement>);
```

### common event types

- ChangeEvent<HTMLInputElement>
- ChangeEvent<HTMLTextAreaElement>
- ChangeEvent<HTMLSelectElement>
- FormEvent<HTMLFormElement>
- MouseEvent<HTMLButtonElement>
- MouseEvent<HTMLDivElement>
- KeyboardEvent<HTMLInputElement>
- FocusEvent<HTMLInputElement>
- FocusEvent<HTMLTextAreaElement>

## types for useRef

basically useRef is like useState except it doesn't re render the components
it is commonly used to reference DOM elements

```tsx
const inputRef = useRef<HTMLInputElement>(null);
```

## Types for context Api

it is a way to store data and have it be accessible for every component in the tree without having to pass it through props

Google it you mf

## types for useReducer

---
# must Know hooks

- useState → manage state in components ✅
- useEffect → side effects (fetch, timers, subscriptions)✅
- useRef → DOM references or persistent values across renders ✅
- useContext → consume context values
- useReducer → manage complex state or multiple state updates
- useMemo → memoize expensive calculations
- useCallback → memoize functions to prevent unnecessary re-renders

---

# React Monster 2 

