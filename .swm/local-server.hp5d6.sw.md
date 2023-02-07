---
id: hp5d6
title: Local server
file_version: 1.1.1
app_version: 1.1.5
---

## Introduction

The way we loaded Three.js in the previous lesson is the easiest. Unfortunately, it has two main limitations.

First, we only have access to “core” classes. There are dozens of classes in this core and we can do a lot with those, but we don’t master everything. As an example, in a future lesson, we are going to need access to the `OrbitControls` class, which is not available in the core classes.

Secondly, when opening an HTML file like this, your browser won’t let JavaScript execute any instructions. As an example, you won’t be able to load local files like textures or models. This is actually a good thing for security reasons. You don’t want a script to be able to load files from your computer just because you opened an HTML file that you thought was safe.

But still, we need to be able to run JavaScript code as if it were an online website and to do that, we need to run a local server.

There are many ways of handling those issues, but the simplest solution is to use a “build tool” or “bundler”.server and doing a bunch of other optimisations for us. If you are not confident about doing that again on your own, don’t worry, we are going to do it together in the next lesson. Again, most of the following lessons have been recorded using Webpack and you might see slight differences. You should be able to ignore those differences.

## **The state of build tools**

There are many build tools available these days and you’ve probably heard of some of them like Webpack, Vite, Gulp, Parcel, etc.

They all have various features with pros and cons, but we are going to use a very specific one in the following lessons.

Nowadays, the most popular build tool is Webpack. It’s widely used, it has a great community and you can do a lot with it. But while Webpack is the most popular, it’s not the most appreciated.

In fact, the most appreciated build tool these days is [Vite](https://vitejs.dev/) (French word for "quick", pronounced `/vit/`, like "veet”). It’s faster to install, faster to run, and less prone to bugs. Ultimately, the developer experience is much better.

## **Vite**

This is not a lesson about Vite.

As mentioned earlier, [Vite](https://vitejs.dev/) is a build tool. The idea is that we are going to write web code like HTML/CSS/JS and Vite will build the final website. It’ll also do a bunch of things like optimizations, cache breaking, source mapping, running a local server, etc.

While Vite handles the most basic needs, we can also add plugins in order to handle more features like exotic languages, or special files. We are actually going to add a plugin later in the course, which will be able to handle GLSL files in order to create custom shaders.

Vite was created by Evan You, the creator of Vue.js, and is highly maintained by hundreds of developers.

## Node.js

First, you need to have Node.js installed on your computer.

Node.js enables running JavaScript on your computer outside of a browser. It’s great to run various tools like Vite, it has been around for many years and is very popular.

If you don’t know if Node.js is already installed or which version is installed, open your Terminal (MacOS) or Command Prompt (Windows) and run `node -v`. If the answer tells you that the node command isn’t recognised, then it’s not installed. If it’s installed, the answer will contain the current version. Make sure it’s updated to the last version. Vite currently works with version 14.18 and above, but I recommend you always have the LTS (Long Term Support) version of Node.js installed.

To install or update Node.js, go to [https://nodejs.org/en/](https://nodejs.org/en/), download the “LTS” and install it with the default settings.

Close your Terminal (MacOS) or Command Prompt (Windows), re-open it, and run node -v again to check the version.

## Dependencies

Now that we are in the project folder, we need to install dependencies. “What dependencies?” you might ask? Well, we have two dependencies with this project: Vite and Three.js.

To install them, run `npm install` from your terminal. Wait for a little while and you should see a node\_modules folder being created in the project folder.

When we installed Node.js, we automatically installed NPM. NPM is a dependency manager that will fetch the dependencies listed in the `📄 package.json` file and install them in the node\_modules folder.

## Run the server

We are almost ready and we can now ask Vite to run the server.

To do so, while still in Terminal and in the project folder, run `npm run dev`.

Wait a second or two and the website should open in your default browser with “Soon to be a Three.js experience” written on the page.

If the page doesn’t open, the terminal should display two URLs that look something like [http://localhost:5173/](http://localhost:5173/) and [http://192.168.1.25:5173/](http://192.168.1.25:5173/). Try them in your browser.

## Troubleshooting

If everything’s worked out, you can skip this section.

If you’ve had issues along the way, I’m going to enumerate some classic troubleshooting and how to fix those issues. Terminal folder Make sure your terminal is opened in the project folder. Use the pwd command to display the folder in which the terminal is currently.

Use the cd (with a space at the end) command, drag and drop the folder, and then press Enter to move the terminal into that folder. Long path If your project folder is nested very deep in other folders, you might end up with a path so long that Node.js can’t handle it.

Move the folder up and make sure to move the Terminal accordingly before trying again. Versioned folder Be careful with tools like OneDrive, Google Drive, Dropbox, etc. that will “save” your files online. They can mess up your Node.js dependencies. Try to move the project outside of those “saved” folders.

Special characters in the path Avoid having special characters in the path from the root of your computer down to the project. Ideally, you should only have lowercase letters, numbers, dashes, and underscores.

### **Terminal folder**

Make sure your terminal is opened in the project folder.

Use the `pwd` command to display the folder in which the terminal is currently.

Use the `cd` (with a space at the end) command, drag and drop the folder, and then press `Enter` to move the terminal into that folder.

### **Long path**

If your project folder is nested very deep in other folders, you might end up with a path so long that Node.js can’t handle it.

Move the folder up and make sure to move the Terminal accordingly before trying again.

### **Versioned folder**

Be careful with tools like OneDrive, Google Drive, Dropbox, etc. that will “save” your files online.

They can mess up your Node.js dependencies.

Try to move the project outside of those “saved” folders.

### **Special characters in the path**

Avoid having special characters in the path from the root of your computer down to the project.

Ideally, you should only have lowercase letters, numbers, dashes, and underscores.

## Permissions

Sometimes, permissions are messed up and NPM can’t install the dependencies. If you know what you are doing, try to fix the permissions. Otherwise, delete the folder, re-download the starter and follow the instructions again.

## More about the Vite template

Here are a few things you need to know about the Vite template before we continue:

The Vite configuration is set in the vite.config.js file. If you are curious about how to configure a Vite project, check the Vite website.

You need to run npm install only once after downloading the project. You need to run npm run dev each time you want to run the server and start coding. Your terminal might seem stuck, but it's perfectly normal, and it means that the server is running. Press CTRL + C to stop the server. You might need to press the shortcut multiple times on a Windows system or confirm with the letter o.

The only folders you need to explore, are the `📄 src` and the static/ folders. In the src/ folder, you can find the traditional index.html, script.js, and style.css files. You can put "static files" in the static/ folder. Those files will be served as if they were available in the root folder (without having to write static/). You can test by adding /door.jpg at the end of the URL (http://localhost:5173/door.jpg). We'll use this to load textures and models later.

The page will automatically reload as you save any of those files.

You can access your local server from any other device on the same network by typing the same URL that looks something like this http://192.168.1.25:5173. It’s very useful to debug on other devices like mobiles. If it’s not working, it’s usually because of your firewall.

## **Get the Three.js scene back**

Here's the easy part. We want to get our Three.js scene back in this Vite template.

First, we need to add the `<canvas>` to the `src/index.html` file:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>04 - Local Server</title>
    <link rel="stylesheet" href="./style.css">
</head>
<body>
    <canvas class="webgl"></canvas>
    <script type="module" src="./script.js"></script>
</body>
</html>
```

Now we need to add the same JavaScript code from the previous lesson in the `/src/script.js` file. The only difference is that we need to import Three.js first.

To import Three.js, we need to write the following line at the very start of the `/src/script.js` file:

```
import * as THREE from 'three'
```

This will import all core classes of Three.js inside the `THREE` variable. The `three` module is in the `/node_modules/` folder, but you don't need to touch it.

Then we can follow with the same code as before:

```
import * as THREE from 'three'

// Scene
const scene = new THREE.Scene()

// Object
const geometry = new THREE.BoxGeometry(1, 1, 1)
const material = new THREE.MeshBasicMaterial({ color: 0xff0000 })
const mesh = new THREE.Mesh(geometry, material)
scene.add(mesh)

// Sizes
const sizes = {
    width: 800,
    height: 600
}

// Camera
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height)
camera.position.z = 3
scene.add(camera)

// Renderer
const renderer = new THREE.WebGLRenderer({
    canvas: document.querySelector('canvas.webgl')
})
renderer.setSize(sizes.width, sizes.height)
renderer.render(scene, camera)
```

If the server was already running, open the page (no need to reload).

If not, run `npm run dev` from the terminal, and the page should open.

And that’s it.

We have the same code as the previous doc running, but this time with a build tool taking care of the local server and doing a bunch of other optimizations for us.

<br/>

This file was generated by Swimm. [Click here to view it in the app](https://app.swimm.io/repos/Z2l0aHViJTNBJTNBVGhyZWVKU19Qcm9qZWN0JTNBJTNBZGFuaWVsYXBhc3Nvcw==/docs/hp5d6).
