<script setup>
    import { ref } from 'vue';
    import GithubSVG from './svg-components/GithubSVG.vue';
    // import LinkContainer from './LinkContainer.vue'; // Adjust the import path as necessary

    const props = defineProps(['entry'])
</script>

<template>
    <div>
        <h3 :style="{ textDecoration: 'underline' }">{{ entry.name }}</h3>
        <h5 :style="{ fontStyle: 'italic' }">
            {{ entry.complete ? '' : 'In progress' }}
        </h5>
        <div :style="{ marginBottom: '1rem'}">
            {{ entry.description }}
        </div>
        <h5>{{ entry.stack }}</h5>
        <!-- <LinkContainer :entry="entry" :isRight="isRight" /> -->
        <GithubSVG :url="entry.githubUrl"/>
    </div>
</template>


<style scoped>
/* You can add component-specific styles here */
.project-card {

}
</style>