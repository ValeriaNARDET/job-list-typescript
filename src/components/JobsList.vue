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
import Job from "@/types/Job";

const props = defineProps<{ sortTitle: string, sortType: string }>();
const { sortTitle, sortType } = toRefs(props);
const jobList = ref<Job[]>([
  { title: 'cowboy', location: 'lon lon ranch', salary: 38000, id: 1 },
  { title: 'quarryman', location: 'death mountain', salary: 47000, id: 2 },
  { title: 'player number one', location: 'the lost woods', salary: 32000, id: 3 },
  { title: 'developer', location: 'Cypres', salary: 21000, id: 4 },
  { title: 'security', location: 'gerudo valley', salary: 32000, id: 5 },
  { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: 6 },
  { title: 'quarryman', location: 'death mountain', salary: 40000, id: 7 },
  { title: 'flute player', location: 'the lost woods', salary: 42000, id: 8 },
  { title: 'fisherman', location: 'lake hylia', salary: 21000, id: 9 },
  { title: 'prison guard', location: 'gerudo valley', salary: 28000, id: 10 },
  { title: 'driver', location: 'death mountain', salary: 23000, id: 11 },
  { title: 'teacher for lama', location: 'gerudo valley', salary: 36000, id: 12 }
])

const sortedJobs = computed(() => {
   return [...jobList.value].sort((a: Job, b: Job) => {
    const st = sortTitle.value as string;
    if (sortType.value === "asc") {
      return a[st] > b[st] ? 1 : -1
    } else {
      return b[st] > a[st] ? 1 : -1
    }
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
  max-width: 900px;
  margin: 50px auto;
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