<script setup>
import Hero from '../components/Hero.vue'
import HomeCarts from '../components/HomeCarts.vue'
import JobsListings from '../components/JobsListings.vue';
</script>

<template>
    <Hero />
    <HomeCarts />
    <JobsListings limit=3 :showButton="true" />
</template>