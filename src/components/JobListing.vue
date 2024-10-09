<script setup>
    import JobData from '@/jobs.json';
    import { defineProps, ref } from 'vue';
    import JobSingle from './JobSingle.vue';

    const jobs = ref(JobData);
    console.log(jobs.value);
        
    defineProps({
        limit: Number
    });
</script>

<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h2 class="text-3xl text-green-500 font-bold mb-6 text-center">
                Brows Jobs
            </h2>
            <div class="grid grid-cols-1 gap-6 md:grid-cols-3">
                <JobSingle v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job"/>
                    
            </div>
        </div>
    </section>
  
</template>
