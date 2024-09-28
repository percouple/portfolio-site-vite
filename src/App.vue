<script setup lang="ts">
import About from './components/main-components/About.vue';
import Connect from './components/main-components/footer/Connect.vue';
import Landing from './components/main-components/Landing.vue';
import ProjectsContainer from './components/main-components/ProjectsContainer.vue';
</script>

<template>
  <div class="flex flex-col justify-center items-center">
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
