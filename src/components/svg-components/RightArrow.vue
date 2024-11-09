<script setup>
const props = defineProps(['url'])
const onClick = () => {
    window.location.href = props.url;
} 
</script>

<template>
    <button class="custom-svg-rules {} mt-2 p-1 border-2" :style="{
        display: props.url ? 'inline-block' : 'none'
    }" @click="onClick">
        <svg 
        xmlns="http://www.w3.org/2000/svg" 
        height="24px" 
        viewBox="0 -960 960 960" 
        width="24px" 
        fill="#e8eaed">
            <path d="M647-440H160v-80h487L423-744l57-56 320 320-320 320-57-56 224-224Z" />
        </svg>
    </button>
</template>

<style scoped></style>