<template>
  <div class="jobs">
    <div class="job" v-for="job in sortedJobs" :key="job.id">
      <h3>{{ job.title }}</h3>
      <p>
        <b>{{ job.salary }}$ </b>
        - {{ job.location }}
      </p>
      
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref, toRefs, defineProps } from 'vue';

interface Job {
  id: number;
  title: string;
  salary: number;
  location: string;
}
const props = defineProps<{ sortType: string }>();
const { sortType } = toRefs(props);

const jobList = ref<Job[]>([
  { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: 1 },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: 2 },
  { title: 'flute player', location: 'the lost woods', salary: 35000, id: 3 },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: 4 },
  { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: 5 },
  { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: 6 },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: 7 },
  { title: 'flute player', location: 'the lost woods', salary: 35000, id: 8 },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: 9 },
  { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: 10 }
])

const sortedJobs = computed(() => {
  return [...jobList.value].sort((a: Job, b: Job) => {
    const st = sortType.value as string;
    return a[st] > b[st] ? 1 : -1
  })
})

</script>

<style scoped>
.jobs {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  grid-auto-rows: 120px;
  grid-auto-flow: dense;
}

.job {
  grid-column: span 2;
  padding: 7px 12px;
  border: 2px solid #42b883;
  border-radius: 6px;
}

.job h3 {
  border-bottom: 1px solid #42b883;
  border-bottom-left-radius: 16px;
}
</style>