<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResourcesButtonMode">Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResourceButtonMode">Add Resource</base-button>
    </base-card>
    <component :is="selectedTab" @addResource="addStoredResource"></component>
</template>
<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: { 
      StoredResources,
      AddResource
   },
    data() {
        return {
            selectedTab: 'stored-resources',
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
    },
    provide() {
        return {
            resources: this.storedResources,
            addResource: this.addStoredResource,
            deleteResource: this.removeResource, 
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
        addStoredResource(title, description, link) {
           const newResource = {
               id: Math.random().toString,
               title: title,
               description: description,
               link: link 
           };
           this.storedResources.unshift(newResource);
           this.selectedTab = 'stored-resources'
        },
        removeResource(resID) {
            const resIndex = this.storedResources.findIndex(res => resID === res.id);
            this.storedResources.splice(resIndex, 1);
        }
    },
    computed: {
        storedResourcesButtonMode() {
            return this.selectedTab === 'stored-resources' ? null : 'flat';
        },
        addResourceButtonMode() {
            return this.selectedTab === 'add-resource' ? null : 'flat';
        }
    }
}
</script>