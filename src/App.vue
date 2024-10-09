<script setup>
  import {ref} from 'vue';
  import NavBar from './components/NavBar.vue';
  import Hero from '@/components/Hero.vue';
  import Homecards from './components/Homecards.vue';
  import JobListing from './components/JobListing.vue';
</script>

<template>
  <NavBar />
  <Hero title="Become a son of bitch" subtitle="Find the Vue job that fits your skills and needs"/>
  <Homecards />
  <JobListing :limit="3"/>
</template>