---
layout: post
title: Install NodeJS, VueCLI and NuxtJS to create a static web site
date: 2021-11-20T09:27:15.691Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/a/ae/Nuxt_logo.svg
---
Install Node Version managager nvm command
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash\n`

List remote NodeJS versions available for install, look for latest LTS
`nvm ls-remote`

Install NodeJS LTS Gallium
`nvm install Gallium`

Install Yarn NodeJS package manager
`npm install --global yarn`

Add VueJS CLI via Yarn
`yarn global add @vue/cli`

Start a Nuxt project
`vue init nuxt/starter <project-name>`

Vue init Credits: 
[https://codeburst.io/create-a-static-site-in-15-minutes-or-less-using-vue-js-e4e2a9945ee6?gi=5b245ce1026b](https://upload.wikimedia.org/wikipedia/commons/a/ae/Nuxt_logo.svg)