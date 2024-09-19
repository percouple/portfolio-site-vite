<script setup>
import { ref } from 'vue';
import ConnectForm from './ConnectForm.vue';
import Footer from './Footer.vue';

const values = ref({
    subject: "",
    message: "",
});

const changeHandler = (e) => {
    const { placeholder, value } = e.target;
    if (placeholder === "Email") {
        values.value.emailAddress = value;
    } else if (placeholder === "Subject") {
        values.value.subject = value;
    } else if (placeholder === "Message") {
        values.value.message = value;
    }
};

const submitHandler = (e) => {
    e.preventDefault();
    const mailtoLink = `mailto:calebsevan@gmail.com?subject=${encodeURIComponent(values.value.subject)}&body=${encodeURIComponent(values.value.message)}`;
    window.open(mailtoLink, 'emailWindow');
};
</script>

<template>
    <div id="connect" class="text-center pb-6">
        <h3 class="text-2xl font-semibold mb-4">Questions? Or looking to collaborate?</h3>
        <h4 class="text-xl font-medium mb-6">Connect with me here!</h4>
        <div class="mx-auto flex justify-center">
            <ConnectForm :changeHandler="changeHandler" :submitHandler="submitHandler" />
        </div>
        <Footer /> 
    </div>
</template>


<style scoped>
</style>