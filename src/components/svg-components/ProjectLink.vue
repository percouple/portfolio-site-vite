<script setup>
const props = defineProps(['url'])

console.log(props.url)
// const urlExists = computed(() => !props.url);

const onClick = () => {
    console.log(props.url)
    window.location.href = props.url;
} 
</script>

<template>
    <button class="custom-svg-rules {} mt-2 p-1 border-2" :style="{ display: props.url ? 'inline-block' : 'none'
    }" @click="onClick">
        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="32" viewBox="0 0 24 24" fill="none" stroke="#BDC4A7"
            stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-log-in">
            <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"></path>
            <polyline points="10 17 15 12 10 7"></polyline>
            <line x1="15" y1="12" x2="3" y2="12"></line>
        </svg>
    </button>
</template>

<style scoped>

</style>