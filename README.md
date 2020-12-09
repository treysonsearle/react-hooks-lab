<img src="https://s3.amazonaws.com/devmountain/readme-logo.png" width="250" align="right">

# Project Summary

This project is geared towards helping you improve your familiarity with React hooks and will function similarly to the original React Drills. We will provided minimal guidance compared to most afternoon projects that offer detailed instructions. When you first go through these set of problems, you may need to look at solutions for help. The goal, however, should be to get to the point where you can complete all sets of problems without any help from solutions and/or mentors.

The solutions provided in this project are just one way you can accomplish the project. If you are curious if your solution is "correct", you can ask a mentor to compare your answer to the ones we are providing.

## Challenge

Once you get to the point where you no longer have to look at the solutions and/or ask mentors for help, time yourself to see how long it takes you to complete all of these sets. After your first time, try to beat that time at least twice. The project is called React Drills for a reason! Repetition will help solidify these React concepts.

## Setup

To help speed up the process of moving from app to app we have provided a bunch of `app-#/` folders that have been created using the `create-react-app` CLI. That way you just have to run `npm install` instead of waiting for `create-react-app`.

- Run `npm install` in each `app-#/` folder before starting the
  - You can either run `npm install` for each `app-#/` before starting app one or just remember to run `npm install` as you move from app to app

You can then test your work for each app, as you develope a solution, by running `npm start` from each `app-#/` folder.

## App #1

Create an application that displays a list of todos and an interface to add a new todo. You will need a few components: `App.js`, `List.js`, `Todo.js`, and `AddTodo.js`. `List.js` will be responsible for rendering a mapped list of todos which will be passed as props from `App.js`. `AddTodo.js` will be responsible for rendering the necessary input and button to make this interface work.

<img src="./images/Hooks%20App%201.gif"  align="center">

<details>

<summary> <code> app-1/src/App.js </code> </summary>

```js
import React, { useState } from 'react'
import List from './components/List'
import AddTodo from './components/AddTodo'
import './App.css'

function App() {
  const [todos, setTodos] = useState([])

  function addTodo(item) {
    const newTodos = [...todos, item]
    setTodos(newTodos)
  }

  return (
    <div className="App">
      <AddTodo addTodo={addTodo} />
      <List list={todos} />
    </div>
  )
}

export default App
```

</details>

<details>

<summary> <code> app-1/src/List.js </code> </summary>

```js
import React from 'react'
import Todo from './Todo'

const List = (props) => {
  return (
    <div>
      {props.list.map((item, index) => {
        return <Todo item={item} key={index} />
      })}
    </div>
  )
}
export default List
```

</details>

<details>

<summary> <code> app-1/src/Todo.js </code> </summary>

```js
import React from 'react'

const Todo = (props) => {
  return <h2>{props.item}</h2>
}
export default Todo
```

</details>

<details>

<summary> <code> app-1/src/AddTodo.js </code> </summary>

```js
import React, { useState } from 'react'

const AddTodo = (props) => {
  const [userInput, setUserInput] = useState('')

  function handleAddTodo(e) {
    e.preventDefault()
    props.addTodo(userInput)
    setUserInput('')
  }

  return (
    <form onSubmit={handleAddTodo}>
      <input
        placeholder="Add a todo!"
        value={userInput}
        onChange={(e) => setUserInput(e.target.value)}
      />
      <button>Submit</button>
    </form>
  )
}
export default AddTodo
```

</details>

<br />
