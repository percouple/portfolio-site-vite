<script setup lang="ts">
import SingleProject from './SingleProject.vue'
import { projectsData } from '../../assets/projectdata';
</script>

<template>
    <div>
        <h2 class="mt-[15rem] scroll-mt-[5rem] ml-[6rem] pl-[14px] pt-[8px] 
        shadow-lg bg-[#222222] max-w-[33%]" id="projects">
            Here's what I've been working on:
        </h2>
        <div class="flex flex-col max-w-[900px] mx-[3rem] mb-[10rem]">
            <div v-for="(entry, index) in projectsData" :key="entry.id"
                :class="index % 2 === 0 ? 'left-project' : 'right-project'">
                <SingleProject :entry="entry" :isRight="index % 2 !== 0" />
            </div>
        </div>
    </div>
</template>

<style scoped>
.left-project {
    padding: 2rem;
    box-shadow: -4px 4px var(--tertiary-color);
    margin-bottom: 2rem;
    text-align: left;
    background-color: #bdc4a7;
    border: 2px solid #222222;
    color: #222222;
    margin-right: 10vw;
    margin-top: 2rem;
    font-size: 1.25rem;
    transition: box-shadow 0.2s, transform 0.2s;
}

.left-project:hover {
    box-shadow: -10px 10px var(--tertiary-color);
    transform: translate(3px, -3px);
}

.right-project {
    padding: 2rem;
    box-shadow: 4px 4px var(--secondary-highlight-color);
    transition: box-shadow 0.2s, transform 0.2s;
    margin-bottom: 2rem;
    text-align: right;
    background-color: #2e2e2e;
    border: 2px solid #222222;
    margin-left: 10vw;
    margin-top: 2rem;
    font-size: 1.25rem;
}

.right-project:hover {
    box-shadow: 10px 10px var(--secondary-highlight-color);
    transform: translate(-3px, -3px);
}
</style>
