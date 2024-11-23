<script setup lang="ts">
import { ref } from 'vue';

const userInput = ref('');
</script>

<template>
    <div className="flex flex-col justify-center items-center h-[100vh] test-borderr">
        <div className="test-borderg max-w-[50%]">
            <div className="font-bold text-3xl ">Welcome! </div>
            <div className="text-md mt-4">Please enter the password you were given with the request</div>
            <input className="max-h-7 mt-6 custom-input" placeholder="password" />
        </div>
    </div>
</template>

<style scoped>
.custom-input {
    color: var(--secondary-color);
    border-bottom: solid 2px var(--secondary-color);
    scrollbar-width: 0px;
    background-color: transparent;
    outline: none;
}
</style>