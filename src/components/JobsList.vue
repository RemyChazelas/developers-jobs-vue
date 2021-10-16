<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name='list' tag='ul'>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="../assets/euro-money.png" alt="a green note in euros
">
          <p>{{ job.salary }} Euros</p>
          <span>{{ job.confidence }} confidence index</span>
        </div>
        <div class="description">
          <p>{{ job.desc }}</p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from 'vue'
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b:Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })
    return {orderedJobs}
  },
})
</script>

<style scoped>
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0;
  }
  .job-list li {
    list-style-type: none;
    background: rgb(20, 20, 20);
    box-shadow: inset 2px 2px 1px #0f0f0f,
            inset -2px -2px 1px #2d2d2d;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: chartreuse;
    font-weight: bold;
    margin: 10px 4px;
  }
  .salary span {
    text-decoration: underline chartreuse;
    font-weight: bold;
    margin: 10px 4px;
    font-size: 0.6rem;
  }
  .list-move{
    transition: all 1s;
  }
</style>