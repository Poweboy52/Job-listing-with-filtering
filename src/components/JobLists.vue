<template>
        <JobCard v-for="(job, index) in data" :key="index" v-bind="job"/>
</template>

<script setup>
    import JobCard from './JobCard.vue';
    defineProps({
        data: Array
    })
</script>

<style scoped>
</style>