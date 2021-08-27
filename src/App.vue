<template>
    <stored-resources :resources="storedResources"></stored-resources>
</template>
<script>
import StoredResources from  './components/learning-resources/StoredResources.vue';

export default {
    components: {
        StoredResources
    },
    data() {
        return {
            storedResources: [
                {
                    id: 'official-guide',
                    title: 'Offical Guide',
                    description: 'This is the official guide of VUE',
                    link: 'https://vuejs.org'
                },
                {
                    id: 'learn-to-google',
                    title: 'Learn to Google',
                    description: 'You should learn how to google',
                    link: 'https://google.org'
                },
            ]
        }
    }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>