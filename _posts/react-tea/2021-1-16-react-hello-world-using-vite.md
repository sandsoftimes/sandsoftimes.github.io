---
layout: post
title: React Hello World using Vite
date: 2021-1-16 20:52:55.000000000 +05:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- React
- Vite
- Web
- Javascript
tags: []
meta:
  _wpas_done_all: '1'
author:
  login: SandsOfTime
  email: janeebee1092@gmail.com
  display_name: SandsOfTime
  first_name: Muhammad
  last_name: Sharjeel Akhtar
permalink: "/2021/1/16/react-hello-world-using-vite"
---
React is one of the readily used framework when it comes to `web` or `mobile` developmenmt.

So far, i've seen two ways of working in react. The first one is the basic one with 
node pakage execute `npx` which will give you the all react framework files and the second one
is with `vite`. Vite provide you the light files structure by excluding all the un-necessary react 
files at the start.

We'll focus on react via using the vite. It is much more reliable and easy to download as all
the files are downloaded in few minutes.

Initially write this on terminal to create the vite project.

```
npm create vite@latest
```

It will ask you to select b/w multiple frameworks. You've to select `react` among them. Then you've to select from the programming languages. 
There will be multiple options e.g Javascript, Typescript. We will go with the Javascript. Then, mention the project name and you are good to go.

You now have the vite react project in your computer. It have multiple files. Initially you have the 3 main files:

* index.html
* App.jsx
* main.jsx

In `index.html` you have your starting root (starting of the DOM). This root will be called from `main.jsx` component. 
The `index.html` looks like this:
```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```
In the body, you've the main `<div id="root">` starting root of the DOM. The div tag is then called in the `main.jsx` file 
so that to make it the root of the DOM (before the call we've just declared it, was not root before). The `main.jsx` file look
like this:
```
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'


ReactDOM.createRoot(document.getElementById('root')).render(
  
    <App />
  
)
```
Here, you can see that we are creating the root by getting the element root from the `index.html` file. And then we are giving 
a `App.jsx` component/function call from this main.jsx component. The `App.jsx` will be returning a basic `h1` tag with the text **What is up?** written in it.
This text will be printed on the screen in the form of h1-heading. `App.jsx` code is as follow:
```
import Chai from "./chai"

function App() {

  return (
    <>
    <Chai/>
    <h1>What is up??</h1>
    </>
  )
  
}

export default App
```

Now to run the project, use this command on your terminal:
```
npm run dev
```

This will be appear in front of you.

![A test image](/assets/images/clt/react-tea/1.png)

