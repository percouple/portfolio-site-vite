<script setup>
    import ProjectLinksContainer from './ProjectLinksContainer.vue';
    const props = defineProps(['entry'])
</script>

<template>
    <div>
        <h3 class="text-2xl mb-2 underline">{{ entry.name }}</h3>
        <h5 class="text-base mb-2 italic">
            {{ entry.complete ? '' : 'In progress' }}
        </h5>
        <div class="text-base mb-1">
            {{ entry.description }}
        </div>
        <h5 class="text-sm font-bold">[{{ entry.stack }}]</h5>
        <ProjectLinksContainer :entry="entry"/>
    </div>
</template>


<style scoped>

</style>