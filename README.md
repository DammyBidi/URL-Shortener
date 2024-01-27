# Frontend Mentor - Shortly URL shortening API Challenge solution

This is a solution to the [Shortly URL shortening API Challenge challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/url-shortening-api-landing-page-2ce3ob-G). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Setup](#Setup)

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size
- Shorten any valid URL
- See a list of their shortened links, even after refreshing the browser
- Copy the shortened link to their clipboard in a single click
- Receive an error message when the `form` is submitted if:
  - The `input` field is empty

### Screenshot

![](/ScreenShot-LiveLink/Screenshot%202024-01-27%20at%2017-01-34%20Shortly%20URL%20shortening%20API%20Challenge.png)
![](/ScreenShot-LiveLink/Screenshot%202024-01-27%20at%2017-03-49%20Shortly%20URL%20shortening%20API%20Challenge.png)


### Links

- Solution URL: [Add solution URL here](https://github.com/DammyBidi/URL-Shortener)
- Live Site URL: [Add live site URL here](https://dammyurlshortener.netlify.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Desktop-first workflow
- [Vue.Js](https://vuejs.org/) - JS library
- [Styled Components](https://styled-components.com/) - For styles

**Note: These are just examples. Delete this note and replace the list above with your own choices**

### What I learned

Vue.js and Front-End Development

Conditional Rendering: Explored the use of v-if and v-show directives to conditionally render elements based on the application's state.

API Integration
Axios for HTTP Requests: Integrated the Axios library to make HTTP requests to a URL shortening API (e.g., TinyURL). Explored how to handle API responses and errors in a Vue.js application.

Error Handling
Form Validation: Implemented form validation to check for empty input fields and displayed error messages to users when necessary. Styled the form to provide visual feedback on validation status.

Problem-Solving
Debugging: Faced and resolved challenges related to CORS issues and Vue.js specific behaviors by using debugging tools and online resources.


### Useful resources

- [Example resource 1](https://tinyurl.com/api-create.php?url=) - I used this API Instead of the https://cleanuri.com/api/v1/shorten as the cleanURL Api isnt working .


## Author

- Website - [Gideon Damilola Bidi](https://github.com/DammyBidi)
- Frontend Mentor - [@DammyBidi](https://www.frontendmentor.io/profile/DammyBidi)
- Twitter - [@Dammy_Bidi](https://twitter.com/Dammy_Bidi)


## Setup

Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


