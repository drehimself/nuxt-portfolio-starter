# Nuxt Portfolio Starter

A simple portfolio starter theme for Nuxt.js static sites. Based on my [Gridsome Portfolio Starter](https://github.com/drehimself/gridsome-portfolio-starter).

![screenshot](https://user-images.githubusercontent.com/4316355/55691365-a2403380-596b-11e9-93be-05b846ec7760.jpg)

## Demo URL

[https://nuxt-portfolio-starter.netlify.app/](https://nuxt-portfolio-starter.netlify.app/)

## Features

- Clean and minimal design
- [Tailwind CSS v1](https://tailwindcss.com)
- Scroll to sections using [vue-scrollto](https://github.com/rigor789/vue-scrollto)
- Blog with markdown content for posts
- Theme Switcher with Dark Mode
- Syntax highlighting with Prism
- 404 Page

## Todo (already done in Gridsome version)

- Basic pagination for posts
- Tags for posts
- Search posts with [Fuse.js](https://fusejs.io) and [vue-fuse](https://github.com/shayneo/vue-fuse)

## Installation

1. Clone the repo and `cd` into it.
1. `npm install`
1. `npm run dev` to start a local dev server.
1. `npm run generate` to build a static site.

## Notes

 - Based on my [personal portfolio website](https://andremadarang.com). I wanted to create an open source version with more features.
 - Check out a [screencast I did](https://www.youtube.com/watch?v=uHo6o1TNQeE) where I go through the process of building my website.
 - Illustrations from [unDraw](https://undraw.co)
 - Search is based on [Fuse.js](https://fusejs.io) and [vue-fuse](https://github.com/shayneo/vue-fuse). It only searches the title and summary of posts for now. Some tweaking may be necessary to get it to search to your liking. Check out the fuse documentation for search settings. [This PR](https://github.com/drehimself/gridsome-portfolio-starter/pull/104) added the ability to search both "Post" and "Documentation" types.
 - Check out these other Gridsome Starters where I got some ideas from:
    - [Gridsome Starter Blog](https://github.com/gridsome/gridsome-starter-blog)
    - [Gridsome Starter Bleda](https://github.com/cossssmin/gridsome-starter-bleda)
    - [Jigsaw Starter Blog](https://jigsaw.tighten.co/docs/starter-templates/) - I got a lot of design inspiration from this starter theme.











# nuxt-portfolio-starter

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
