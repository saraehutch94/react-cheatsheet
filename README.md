## React Cheatsheet

*React DevTools for Google Chrome will help inspecting your component state + JSX code*

### What is React?

- A toolkit that allows you to build the part of the website that users see and interact with.
- React is a JavaScript library (think of jQuery)
- JavaScript library for building user interfaces
- More efficient than writing in vanilla JavaScript
- **Declarative programming library** - uses functions/functional programming
- **Component-based** - components give us a way to break down the user interface into smaller pieces (ex: nav bar could be one component, an article on the page could be a component, logo could be a component, etc.)
- React is unopinionated (only thing you need to continue to do is add your components inside the **src** folder)

---

### React in code

- React is written in JavaScript
- Uses special language called **JSX** (HTML-JavaScript hybrid / HTML-esque syntax for React) - helps define structure of DOM using familiar HTML syntax
- **JSX = JavaScript in XML** - JavaScript extension to XML specification - defines markup / describes how front end will look

---

### Start React Application

```
npx create-react-app hello-world
```

- **npx** - task runner (built-in with Node.js + npm) --> makes sure we always get the most up-to-date version of `create-react-app`
- Creates `hello-world` folder, so to head into this folder just cd into it and open it using your text editor
- As soon as this builds, the create-react-app build tool is taken off computer

---

### React File System

- Gives us local gitignore file
- Initialize Git repo for us
- Within package.json you can see what version of React that the build created
-- **React DOM** - secondary library that React uses to communicate with your browser (glue between React and browser)
-- React scripts (ex: `npm start`)
- Application entry point/root sits inside of src directory --> `index.js` - where React and browser come together and connect
- `ReactDOM.render` takes `<App />` component and injects it into the DOM (`document.getElementById('root')`)
-- Within **public folder**, there is an `index.html` file in there --> this is the one and only HTML file that a React app will ever use; this is where you will find the `div` with the id of 'root'

---

### Why React?
- React gives us the ability to create a **SPA - single page application**
- Only one HTML document gets served to the browser
- Once React is rendered to browser, the JavaScript begins to run + takes over
- Gives you appearance that you are moving across multiple pages but you are actually just on one page --> **client-side routing**
-- JavaScript is doing all the work when the page "changes"

---

### Run your React app

`npm start` --> runs React app on browser, will pop up automatically in browser

---

### App.js

- Everything you will see in the browser at the start of running the React app (React logo spinning, etc.)
- You can take everything out of this App.js component (only take code out of the `div` with the class of 'App')
- Can also take out logo import at top of file
- Test: within this `div` write out a Hello World using a header, like this:

```
function App() {
    return (
        <div className="App">
            <h1>Hello World</h1>
        </div>
    );
}
```
- If you head to your browser, you will see the changes
-- React uses **Hot Refresh** --> similar to what `nodemon` would do (doesn't re-start development server, it refreshes it)
- If JSX code is difficult, head to Language Mode (command + shift + P) and start typing Language --> click on **Change Language Mode**
- Click on **Configure File Association for '.js'**
- You will see a bunch of options. Type React and you will see **JavaScript React**
- You may need to close VSCode tab and re-open it for it to start working again

### React Components

- React components (ex: `<App />`) are expressed as JavaScript functions, as seen in the codeblock above
- You can use function declaration (above) or expression (arrow function) syntaxes
- *A great practice to use is keeping your components as function declarations and your helper functions as function expressions*
- **Components return a part or all of the user interface**
- **A component takes data as input and renders that data as a user interface**
- `F(D) -> V` function that takes data and returns view/user interface
- React components can only be returned as a single node
- You need to return your component content within **one JSX tag** (`div` below holding all content), like this:

```
function App() {
    return (
        <div>
            <h1>Hello World</h1>
            <p>Hello React</p>
            <p>Hello Sara</p>
        </div>
    );
}
```

- You can't do this:

```
function App() {
    return (
        <h1>Hello World</h1>
        <p>Hello React</p>
        <p>Hello Sara</p>
    );
}
```

- You can also wrap all your content with a **JSX fragment** without introducing new elements to the DOM, such as the `div` above:

```
function App() {
    return (
        <>
            <h1>Hello World</h1>
            <p>Hello React</p>
            <p>Hello Sara</p>
        </>
    );
}
```

- Self-closing tags need to have the backslash before the end carrot. They won't compile if not:

```
function App() {
    return (
        <div>
            <h1>Hello World</h1>
            <p>Hello React</p>
            <p>Hello Sara</p>
            <br />
            <img src="" alt="" />
            <input type="text" />
        </div>
    );
}
```

- Each JSX is it's own function that return the resulting HTML you see in the browser (called **built-in components**)
- `<App />` is defined as a **user-defined component**

---

### React Components

#### Creating, exporting + importing

- We want to create a separate folder to put all of our React components in, such as the nav bar, main area, etc.
- Within the **src** folder, add a folder called **components**
- Add all your component files to this folder
- A common convention when it comes to naming files and components in React is to capitalize your component file names (ex: Header.js) as well as the components themselves (ex: `function Header`)
- Add your component function within the file, like this:

```
function Header() {
    return (
        <header>
            <h1>Header Text/Content</h1>
        </header>
    );
}
```

- We want to require our components in other files, we want to **export** it. Export your components below your component function call like this:

```
export default Header;
```

- If you had multiple functionalities to export from a component file, you would want to do a **named export** with comma separation, like so:

```
export { Header, etc... };
```

- To import your exported components, we want to add the import statement to the component where you want it to be rendered to the DOM (for example, the **App** component):

```
import Header from './components/Header';
```

- Whenever we are rendering components, we need to write them out inside a JSX fragment and use the capitalization convention mentioned above; and this is a self-closing tag, so we need to add the backslash and closing carrot
- Writing this out is basically like invoking a function, like this: `Header()`:

```
function App() {
    return (
        <>
            <Header />
        </>
    );
}
```

- *Hint:* in VSCode, if press **command** and hover over your components (`<Header />`, `<Footer />`, etc.), you will get a link you can click on to head to that component's code file

#### Injecting JavaScript code into JSX of component

- If you wanted to inject JavaScript code into your JSX, you can use curly braces. For example, let's say we wanted to add the current year to a footer:

```
<footer>
    <p>Copyright &copy; All Rights Reserved { new Date().getFullYear() } </p>
</footer>
```

#### Component Props

- **Props** (also called **JSX attributes**) are used to transmit or provide data to our components
- They resemble HTML attributes and can be named whatever you want:
- Example below: The `whichPlayer` prop is added to each `<Player />` to determine which player is X and which player is O

```
function App() {
    return (
        <>
            <Header />
            <Player whichPlayer="X" />
            <Player whichPlayer="O" />
            <Footer />
        </>
    )
}
```

- To access these props within the component you are passing them to, you add `props` to your component function as a parameter
- You can access these props within the function code by utilizing curly braces (inserting JS into JSX) and then accessing the prop name by using dot notation on the passed down the props argument:

```
function Player(props) {
    return (
        <div>
            <h2>Player: { props.whichPlayer }</h2>
            <h3>Wins: { props.whichPlayer }</h3>
        </div>
    );
}
```

#### More on Props

- **Props** are passed from **parent component to child component** - never the other way around
- React data flow is unidirectional and can only be passed down --> data can never be directly passed from child to parent or from sibling to sibling
- Props are organized into a single object within the child component, this is why we used dot notation to access the prop attributes
- **Props are immutable** --> they cannot be assigned a new value within the child component receiving the prop
- Props are written in a `name=value` format, similar to HTML attributes
- If you create props to pass down to a component, you can view the props in your React DevTools. You will see that the prop has been turned into an object, with the key being the name of the prop and the value being the value you gave the attribue/prop (`key: value` pairs):

```
{
    title: 'Santorini',
}
```

