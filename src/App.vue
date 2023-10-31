<template>
  <div class="app">
    <header>
      <div class="title">
        <!-- <img src="./assets/heart.svg" alt="site logo"> -->
        <h1>Job Index</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Sort by title</button>
        <button @click="handleClick('salary')">Sort by salary</button>
        <button @click="handleClick('location')">Sort by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
import JobList from './components/JobList.vue'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Agricultural Engineer', location: 'Copenhagen', salary: 45000, id: '2' },
  { title: 'Data Scientist', location: 'Aarhus', salary: 35000, id: '3' },
  { title: 'Business Analyst', location: 'Odense', salary: 42000, id: '4' },
  { title: 'Bakery Staff', location: 'Esbjerg', salary: 38000, id: '5' },
  { title: 'Software Engineer', location: 'Aalborg', salary: 36000, id: '6' },
  { title: 'Biomedical Scientist', location: 'Roskilde', salary: 41000, id: '7' },
  { title: 'Farm Laborer', location: 'Horsens', salary: 31000, id: '8' },
  { title: 'IT Technician', location: 'Viborg', salary: 40000, id: '9' },
  { title: 'Bakery Assistant', location: 'Randers', salary: 34000, id: '10' },
  { title: 'Farm Manager', location: 'Kolding', salary: 50000, id: '11' }
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, order, handleClick }
  }
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
