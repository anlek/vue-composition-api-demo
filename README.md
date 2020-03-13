# Vue Composition API demo

## Demo details

This demo was presented at the Yukon Tech Collective meetup on March 12th, 2020. It shows the difference between Vue 2.0's Options API vs Vue 3.0's Composition API component design.

Composition API that we're using is back ported to Vue 2.0 with a few gotchas. Read more on [Composition API](https://vue-composition-api-rfc.netlify.com/)

Also any if you want to learn about [Vue](https://vuejs.org/), you can learn more at the [guides](https://vuejs.org/v2/guide/).

### Compiles and hot-reloads for development

```
yarn serve
```

then visit [http://localhost:8080](http://localhost:8080/)

### Lints and fixes files

```
yarn lint
```

#### Auto correct linting with Prettierx

During the demo, I talked about the auto fixing of my JS code, this is done via [Prettierx](https://github.com/brodybits/prettierx)

This project defines a `.prettierrc.json` file that denotes how to Andrew likes his Javascript code to look like and make those changes automatically. `Prettierx` is used (vs `Prettier`) because Prettierx gives a few more options that are important for me.

Read more on [prettier](https://prettier.io) and [prettierx](https://github.com/brodybits/prettierx)
