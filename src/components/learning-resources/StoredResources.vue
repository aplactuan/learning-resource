<template>
    <the-header title="Learning Resources"></the-header>
    <ul>
        <learning-resource 
            v-for="res in resources" 
            :key="res.id" 
            :title="res.title"
            :description="res.description"
            :link="res.link"
        ></learning-resource>
    </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
import TheHeader from '../layouts/TheHeader.vue';

export default {
    components: {
        LearningResource,
        TheHeader
    },
    props: ['resources']
}
</script>

<style scoped>
 ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}   
</style>