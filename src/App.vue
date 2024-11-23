<script setup lang="ts">
import About from './components/main-components/About.vue';
import Connect from './components/main-components/footer/Connect.vue';
import Landing from './components/main-components/Landing.vue';
import PasswordPage from './components/main-components/PasswordPage.vue';
import ProjectsContainer from './components/main-components/ProjectsContainer.vue';
import { ref } from 'vue';

const authenticated = ref(false);
</script>

<template>
  <div v-if="!authenticated">
    <PasswordPage :authenticated="authenticated" />
  </div>
  <div v-if="authenticated" class="flex flex-col justify-center items-center">
    <!-- NavBar -->
    <!-- BodyWithSide -->
    <!-- Social Links -->
    <Landing />
    <About />
    <!-- Projects -->
    <ProjectsContainer />
    <!-- Connect -->
    <Connect />
    <!-- BodyWithSide -->
  </div>
</template>

<style scoped></style>
