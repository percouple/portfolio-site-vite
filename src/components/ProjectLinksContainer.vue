<script setup>
    import GithubSVG from './svg-components/GithubSVG.vue';
    import ProjectLink from './svg-components/ProjectLink.vue';
    const props = defineProps(['entry'])
</script>

<template>
    <div class="w-full mt-2 flex flex-start">
        <GithubSVG :url="entry.githubUrl" class="mr-4"/>
        <ProjectLink :url="entry.url"/>
    </div>
</template>


<style scoped>

</style>