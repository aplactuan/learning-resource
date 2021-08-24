<template>
    <ul>
        <learning-resource 
            v-for="res in storedResources" 
            :key="res.id" 
            :title="res.title"
            :description="res.description"
            :link="res.link"
        ></learning-resource>
    </ul>
</template>
<script>
import LearningResource from './components/learning-resources/LearningResource.vue';

export default {
    components: {
        LearningResource
    },
    data() {
        return {
            storedResources: [
                {
                    id: 'official-guide',
                    name: 'Offical Guide',
                    description: 'This is the official guide of VUE',
                    link: 'https://vuejs.org'
                },
                {
                    id: 'learn-to-google',
                    name: 'Learn to Google',
                    description: 'You should learn how to google',
                    link: 'https://google.org'
                },
            ]
        }
    }
}
</script>