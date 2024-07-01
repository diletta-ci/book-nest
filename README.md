# Book Nest

Experiment Vue3 micro-frontend application to buy and sell your second-hand books.


## Development
Launch commands in the terminal on main wrapper app (book-nest-wrapper) and each micro-frontend apps and open http://localhost:8080 on your browser.

```
npm i
npm run start
```


### Micro-frontend
1. Create the micro-frontend
To create a new micro-frontend app launch the command
```npx create-mf-app app-name```

2. Expose the component of the remote app
`remote/webpack.config.js`
```
exposes: {
    "./MyNewComponent": "./src/components/MyNewComponent/MyNewComponent.vue"
},
```

3. Import the new component on the main wrapper app
`book-nest-wrapper/webpack.config.js`
```
remotes: {
    remote: "upload_book@http://localhost:8081/remoteEntry.js?v=[Date.now()]"
},
```

Now you can use the component in the main wrapper app
`App.vue`
```
<template>
  <div>
    <div>BookNest</div>
    <MyNewComponent />
  </div>
</template>

<script setup>
  import MyNewComponent from 'remote/MyNewComponent'
</script>
```


#### Current Status
Early phase, just starting up the project.