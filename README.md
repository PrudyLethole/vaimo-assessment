# assessment

## Project setup
```
npm install
```
npm install axios

npm install sass@~1.32 sass-loader deepmerge -D

npm install vuetify

npm i @vue/cli-service

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Achitecture

The project is structured as follows:

I have a created a component called AssessmentData.vue  under the components folder, which has a template of the whole project and fetch data from the provided API.

I have created a file called App.vue in which i imported the components/Assessment.vue in.

### Which stacks i used and why

I have used vue.js although I have never used it, while building the project with it I have come to the reliasation that you can easily create differeny types of components and reuse them at a later stage and i also like its simplicity.

If i were to do it again, I will still choose Vue.js because I believe the more I practice is the more I will get better with it and also because of its reusability, if I create a hero component which i would like to use again in a separate page, I dont have to repeat the code, I simply have to import the one that is available.