<script setup>
  import Hero from '@/components/Hero.vue';
  import Homecards from '@/components/Homecards.vue';
  import JobListing from '@/components/JobListing.vue';
</script>

<template>
    <Hero title="Become a son of bitch" subtitle="Find the Vue job that fits your skills and needs"/>
    <Homecards />
    <JobListing :limit="3" :showButton="true"/>
</template>