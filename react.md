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
  const items = [
    'Bag',
    'Laptop',
    'Boxed tees',
    'Baggy Trousers',
    'Skin Care',
    'Iphone',
    'Dog',
    'Dog Cage',
    'Cat',
    'Cat supplies',
  ];
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

---

- start time : 7:09pm (1:49:03)
- stop time : 2:49:03
- goal : 3:58:08
