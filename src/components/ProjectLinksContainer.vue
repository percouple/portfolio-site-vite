<script setup>
    import GithubSVG from './svg-components/GithubSVG.vue';
    import ProjectLink from './svg-components/ProjectLink.vue';
    const props = defineProps(['entry'])
</script>

<template>
    <div>
        <GithubSVG :url="entry.githubUrl"/>
        <ProjectLink :url="entry.url"/>
    </div>
</template>


<style scoped>

</style>