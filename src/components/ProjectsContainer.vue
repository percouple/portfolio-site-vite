<script setup lang="ts">
    import { ref } from 'vue';
    import Project from './SingleProject.vue'
    import { projectsData } from '../assets/projectdata';
</script>

<template>
    <div>
        <h2 class="project-header" id="projects">
            Here's what I've been working on:
        </h2>
        <div class="project-container">
            <div v-for="(entry, index) in projectsData" :key="entry.id"
                :class="index % 2 === 0 ? 'left-project' : 'right-project'">
                <Project :entry="entry" :isRight="index % 2 !== 0" />
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>
