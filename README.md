# Scope
- Starting a Vue Project with Vue CLI 3
- Understanding how to communicate between parent and children components
- First touch with VUE Directives

## Initialization of a vue project
Run in command line
```
vue create <projectname>
```
Select ` default (babel, eslint) ` since the very project wont need any other features such as `vue router`

## Structure of a vue file

```
<template>
Define your html in here
</template

<script>
Import statements

export default {
    name: 'App',                    <-- A wise man told me nothing is more important than naming
    components: {                   <-- List all the importent components
        Searchbar,
        VideoList,
        VideoDetail
    },
    data (){                        <-- Data defines the initial state of the application 
        return {
            videos: [],
            selectedVideo: null
        }
    },
    methods: {                      <-- Define the way the different ways the state of your application can be changed
        onVideoSelect(video){
          this.selectedVideo = video
        }
    },
    props:{                         <-- Data that is being send from a parent component to a child component
        video: Object
    },
    computed:{                      <-- Define how to turn the current data into viewable values
        videoUrl(){
            const {videoId} = this.video.id
            return `https://www.youtube.com/embed/${videoId}`
        }
    }
}
</script>

<style scoped>
Define your css styling in here (Use scoped so you don't apply the css styling to the whole project
</style>
```

## Projectstructure

```
├── index.html
├── public
│   └── favicon.ico
│   └── index.html
├── src
│   └── APP.vue
│   └── components
│         └── Searchbar.vue
│         └── VideoDetail.vue
│         └── VideoList.vue
│         └── VideoListItem.vue
├── main.js
├── package.json
└── vue.config.js
```
### main.js
```
import Vue from 'vue'
import App from './App'

new Vue ({
    // el: '#app',
    render : h => h(App)
}).$mount('#app')
```
Inside the main.js file a new vue instance is being create. Since we want to render our Application, we are import it and mount it to the very root `<div>` which has the `id="app"` inside the `index.html` file.

Another way of rendering the Application:
```
new Vue ({
    render: function(createELement) {
        createElement(App) }
        }
```



# How to start the Project

## Development Build
```
npm install
npm run serve
```

### Production Build
```
docker build . -t <YOUR_IMAGE_NAME>
docker run -it -p 3000:80 <YOUR_IMAGE_NAME>
```



### Lints and fixes files
```
npm run lint
```

