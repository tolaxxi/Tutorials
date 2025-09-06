# React

A JavaScript library for building user interfaces

## installing react

```bash
  npm create vite@latest
```

## folder structure

1. node_modules/: contains all the module and packages your project need to run

2. public/: where we put all our assets files

3. src/:the heart of our project

4. src/assests : where we pt all our images

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



 

start time : 1:51am (0.00)
stop time :
