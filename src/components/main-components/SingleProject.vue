<script setup>
    import ProjectLinksContainer from './ProjectLinksContainer.vue';
    const props = defineProps(['entry'])
</script>

<template>
    <div>
        <h3 class="text-2xl underline">{{ entry.name }}</h3>
        <h5 class="text-base italic">
            {{ entry.complete ? '' : 'In progress' }}
        </h5>
        <div class="text-base mb-1 mt-6">
            {{ entry.description }}
        </div>
        <div class="flex justify-between items-center mt-2">
            <ProjectLinksContainer :entry="entry"/>
            <h5 class="text-sm font-bold hidden sm:flex">[{{ entry.stack }}]</h5>
        </div>
    </div>
</template>


<style scoped>

</style>