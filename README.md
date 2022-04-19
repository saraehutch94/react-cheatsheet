## React Cheatsheet

#### What is React?

- A toolkit that allows you to build the part of the website that users see and interact with.
- React is a JavaScript library (think of jQuery)
- JavaScript library for building user interfaces
- More efficient than writing in vanilla JavaScript
- **Declarative programming library** - uses functions/functional programming
- **Component-based** - components give us a way to break down the user interface into smaller pieces (ex: nav bar could be one component, an article on the page could be a component, logo could be a component, etc.)

---

#### React in code

- React is written in JavaScript
- Uses special language called **JSX** (HTML-JavaScript hybrid / HTML-esque syntax for React) - helps define structure of DOM using familiar HTML syntax
- **JSX = JavaScript in XML** - JavaScript extension to XML specification - defines markup / describes how front end will look

---

#### Start React Application

```
npx create-react-app hello-world
```

- **npx** - task runner (built-in with Node.js + npm) --> makes sure we always get the most up-to-date version of `create-react-app`
- Creates `hello-world` folder, so to head into this folder just cd into it and open it using your text editor
- As soon as this builds, the create-react-app build tool is taken off computer

---

#### React File System

- Gives us local gitignore file
- Initialize Git repo for us
- Within package.json you can see what version of React that the build created
-- **React DOM** - secondary library that React uses to communicate with your browser (glue between React and browser)
-- React scripts (ex: `npm start`)
- Application entry point/root sits inside of src directory --> `index.js` - where React and browser come together and connect
- `ReactDOM.render` takes `<App />` component and injects it into the DOM (`document.getElementById('root')`)
-- Within **public folder**, there is an `index.html` file in there --> this is the one and only HTML file that a React app will ever use; this is where you will find the `div` with the id of 'root'

---

#### Why React?
- React gives us the ability to create a **SPA - single page application**
- Only one HTML document gets served to the browser
- Once React is rendered to browser, the JavaScript begins to run + takes over
- Gives you appearance that you are moving across multiple pages but you are actually just on one page --> **client-side routing**
-- JavaScript is doing all the work when the page "changes"

---

#### Run your React app

`npm start` --> runs React app on browser, will pop up automatically in browser

---

#### App.js

- Everything you will see in the browser at the start of running the React app (React logo spinning, etc.)
- You can take everything out of this App.js component (only take code out of the `div` with the class of 'App')
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
- If JSX code is difficult, head to Language Mode (command + shift + P) and start typing Language --> click on **Change Language Mode**
- Click on **Configure File Association for '.js'**
- You will see a bunch of options. Type React and you will see **JavaScript React**
- You may need to close VSCode tab and re-open it for it to start working again