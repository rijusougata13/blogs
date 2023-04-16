---
title: "Get Started With React -  Beginner's Guide"
datePublished: Mon Mar 13 2023 19:38:06 GMT+0000 (Coordinated Universal Time)
cuid: clf788od2000s0al1d96c5deo
slug: get-started-with-react-beginners-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678648534112/7113394c-b76c-44e6-b3db-539bd668fdb4.jpeg
tags: javascript, technology, reactjs

---

If you want to start learning React.js but you are a complete beginner, then you came to the right place. Today I will discuss how to get started with react, and the basic things you need to understand. After reading this blog you will have a clear understanding of how react.js works 🎢.

### What is React and why it is so popular? 🤩

React is an open-source free frontend javascript library for developing UI components. If you see the stats you can find React is currently top used ui library for frontend development. Some of the reasons are:

* **Easy To Grasp:** If you are a completely new programmer, it will not be too hard to grasp the knowledge about react and get started with it. Many companies prefer to use React in their frontend stack as if they have any new joiner he/she can easily get started with React and contribute to development.
    
* **Open Source:** React is completely open-sourced, so it is well backed up and it has vast library support. You can easily find over 2 Lakhs React packages in npm.
    
* **Virtual DOM:** React supports virtual dom which makes the user experience better. React renders the DOM (Document Object Model) virtually first as a copy of the actual DOM. So it only makes changes which are necessary through virtual DOM. This makes page loading and updating faster and brings a good experience.
    

### How to install react app and what are the prerequisites?

To install react you should have node js installed on your machine. How to check if your machine has node js installed or not? Just open a command prompt and type `node -v` if this gives an error you can install node js from [here](https://nodejs.org/en/download/) and follow the instruction. We will be using [create-react-app](https://create-react-app.dev/) for developing and getting started with react. For this, you should have a node version not less than v14.0 and npx version not less than v5.6. Do update those dependencies before creating react application.

But the question is what is ***create-react-app 🙋‍♂️***?

Creating a react app is a very time-consuming process. If you want to set up a react app without the help of create-react-app, it takes a lot of time and effort and you need to do lots of configuration to get started. So create-react-app helps us to automate this configuration and working directory setup.  
You just have to run `npx create-react-app appName` and it will automatically create a folder called `appName` which contains the react code.

**Note:** `appName` is a variable name. You can put whatever you want.

### After installing react app what's next?

Congratulations 🤩 on successfully installing your first react app!! Now, let's start our application.  
go to the `appName` directory by `cd appName` and then run `npm start` to start your application. You if head over to `locahost:3000` you can see your react app successfully running.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678650924857/9d70bf97-d7fa-48bd-8cfe-0f0a377eee22.png align="center")

Now let me explain the directory structure. If you open `appName` folder would be similar to this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678651103192/806f34a2-659c-432f-9195-ed88187290a6.png align="center")

**node\_modules:** it is the place where you install all your dependencies. when you run `npm run package-name` it installs the package in the node\_modules folder. if you expand node\_modules you can find all of your packages.

**public:** Though you will mostly work in the src folder, this public folder contains some static files like index.html. It's the end result of what we compile. You can modify your app name or add fonts styling or add cdn and many more here.

**src:** Here you will spend most of your time. It contains App.js, index.js and your other component files.

**package.json:** It is the configuration file of your application. If you want to modify anything you can do it here.

**src/App.js:** Here you will declare all your components. It's the best practice to create a separate folder for your components and import those in App.js

**src/index.js:** This is the entry point of your react application.

### What's JSX? Do I need to learn it?

In React if you are not using JSX it's pretty hard to build a component. For a simple div itself, you have to use `React.createElement`. So here JSX comes to help. It's a Javascript extension syntax which helps us to write html and javascript together. So It makes it easier to write code in React.

```javascript
class Hello extends React.Component {
  render() {
    return <div>Hello {this.props.toWhat}</div>;
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Hello toWhat="World" />);
```

```javascript
class Hello extends React.Component {
  render() {
    return React.createElement('div', null, `Hello ${this.props.toWhat}`);
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(React.createElement(Hello, {toWhat: 'World'}, null));
```

Here you can clearly see the difference. JSX makes writing code easier. But don't worry [`create-react-app`](https://github.com/facebook/create-react-app) internally uses Babel for the JSX to JavaScript conversion so in the end, the later one is the final output.

### What's next then 😄?

First of all congrats for reaching out this far. You already covered the basics of react now I would recommend going create a react application and playing with it. Don't be afraid to add or modify anything as it's the only way to learn new technologies.

### Conclusion 🥳

In this article, you learnt what is react, how to install and create a react app, learnt about the directory structure and JSX. In the next blog, I will cover more details about React. Till then don't stop learning new things and don't get demotivated. Will see you in the next blog.

If you enjoyed this article, you can support me by [buying me a coffee](https://www.buymeacoffee.com/rijusougata13) and following me on [twitter](https://twitter.com/rijusougata13).