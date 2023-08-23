<template>
  <div class="main-heading-wrapper">
    <h2>Choose your job:</h2>
  </div>

  <div class="actions">
    <button @click="sortJobs('title')">Sort by Title</button>
    <button @click="sortJobs('salary')">Sort by Salary</button>
    <button @click="sortJobs('location')">Sort by Location</button>
  </div>

  <div class="jobs-wrapper">
    <JobsList :sortType="sortType" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import JobsList from "@/components/JobsList.vue";

type SortType = "title" | "salary" | "location";

const sortType = ref<SortType>("title");

function sortJobs(sType: SortType) {
  sortType.value = sType;
} 
</script>
