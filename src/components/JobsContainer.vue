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
    <JobsList :sortTitle="sortTitle" :sortType="sortType" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import JobsList from "@/components/JobsList.vue";
import SortTitle from "@/types/Sort";

const sortTitle = ref<SortTitle>("title");
const sortType = ref<string>("asc");

function sortJobs(st: SortTitle) {
  if (sortTitle.value === st) {
    sortType.value = sortType.value === "asc" ? "desc" : "asc"
  } else {
    sortType.value = "asc";
    sortTitle.value = st;
  }
} 
</script>

<style scoped>
h2 {
  color: #42b883;
}

button {
  margin: 12px;
  padding: 8px 16px;
  border: 0;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 700;
  color: #f9f9f9;
  background-color: #42b883;
  box-shadow: 0 3px 12px rgba(0, 0, 0, .07), 0 1px 4px rgba(0, 0, 0, .07);
}
</style>