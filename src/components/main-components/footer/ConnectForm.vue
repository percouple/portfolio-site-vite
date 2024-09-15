<script setup>
import { ref } from 'vue';

const form = ref({
    email: '',
    message: '',
});

const errors = ref({
    email: '',
    message: '',
});

const isSubmitting = ref(false);
const successMessage = ref('');

const handleSubmit = async (event) => {
    event.preventDefault();
    isSubmitting.value = true;

    try {
        const response = await fetch('https://formspree.io/f/manwnjpz', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify(form.value),
        });

        if (response.ok) {
            successMessage.value = "Thanks for reaching out! I'll get back to you within 2 business days.";
            form.value = { email: '', message: '' }; // Clear the form
        } else {
            const data = await response.json();
            errors.value = data.errors.reduce((acc, error) => {
                acc[error.field] = error.message;
                return acc;
            }, {});
        }
    } catch (error) {
        console.error('Form submission error:', error);
    } finally {
        isSubmitting.value = false;
    }
};
</script>

<template>
    <div>
        <form @submit.prevent="handleSubmit" class="flex flex-col mr-8 justify-between h-48">
            <input v-model="form.email" id="email" type="email" name="email" placeholder="email"
                class="min-h-5 outline-none p-2 border rounded mb-2" />
            <p v-if="errors.email" class="text-red-500 text-sm">{{ errors.email }}</p>

            <textarea v-model="form.message" id="message" name="message" placeholder="message"
                class="min-h-20 min-w-40 outline-none p-2 border rounded mb-2" />
            <p v-if="errors.message" class="text-red-500 text-sm">{{ errors.message }}</p>

            <button type="submit" :disabled="isSubmitting"
                class="min-h-8 min-w-40 bg-blue-500 text-white font-medium py-2 px-4 rounded hover:bg-blue-600 disabled:opacity-50">
                Connect!
            </button>

            <p v-if="successMessage" class="text-green-500 mt-2">{{ successMessage }}</p>
        </form>
    </div>
</template>


<style scoped>
/* Tailwind CSS classes are used, so no additional styles needed */
</style>