<script setup>
import { ref } from 'vue';

// State for the form elements
const form = ref({
    email: '',
    message: '',
});

// State for the error messages
const errorMessage = ref('');
const isSubmitting = ref(false);
const successMessage = ref('');
const submitDisabled = ref(true);

const handleSubmit = async (event) => {
    event.preventDefault();

    if (currentField.value === 'message' && form.value.message) {

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
                currentField.value = 'success';
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

        // Set the field back to email
        setTimeout(() => {
            currentField.value = 'email';
        }, 4000)
    }
};

const currentField = ref('email');

const switchField = () => {
    switch (true) {
        case currentField.value === 'email': {
            if (form.value.email.match(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/)) {
                currentField.value = 'message'
            } else {
                errorMessage
            }
            break;
        }
        case currentField.value === 'message': {
            break;
        }
    }
}
</script>

<template>

    <form @submit.prevent="handleSubmit" class="flex flex-col justify-between h-48">
        <!-- User Email field -->
        <Transition name="slide-fade">
            <div v-if="currentField === 'email'">
                <input v-model="form.email" id="email" type="email" name="email" placeholder="Type your email address"
                    class="custom-input min-h-5 bg-transparent outline-none p-2 mb-2" />
            </div>
        </Transition>

        <!-- User message field -->
        <Transition name="slide-fade">
            <div v-if="currentField === 'message'">
                <textarea v-model="form.message" id="message" name="message" placeholder="message"
                    class="custom-input min-h-24 min-w-40 bg-transparent outline-none p-2 mb-2" />
            </div>
        </Transition>

        <!-- Submit Button -->
        <p v-if="errorMessage" class="text-red-500 text-sm">{{ errorMessage }}</p>

        <div>
            <div v-if="currentField === 'message' && form.message">
                <button type="submit" :disabled="isSubmitting" class="custom-submit-button min-h-8 min-w-40 font-medium py-2 px-4 
                    rounded disabled:opacity-50">
                    Connect!
                </button>
            </div>
            <button v-if="currentField === 'email'" @click="switchField">Right Arrow</button>
        </div>

        <p v-if="currentField === 'success'" class="mt-2">{{ successMessage }}</p>
    </form>

</template>


<style scoped>
.custom-submit-button {
    background-color: var(--tertiary-highlight-color);
    color: var(--primary-color);
}

.custom-input {
    color: var(--secondary-color);
    border-bottom: solid 2px var(--secondary-color);
    scrollbar-width: 0px;
}

.slide-fade-enter-active {
    transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
    /* transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1); */
    transition: all 0.8s ease-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    transform: translateX(-20px);
    opacity: 0;
}
</style>