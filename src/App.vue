<template>
  <div class="app">
    <!-- <p>name: {{ name }} - age: {{ age }}</p>
    <button @click="changeName('zelda'), changeAge(0)">change name + age</button> -->
    <!-- <p>{{ jobs[0].location }}</p> -->
    <header>
      <div class="title">
        <h1>Tech Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order By Title</button>
        <button @click="handleClick('salary')">Order By Salary</button>
        <button @click="handleClick('location')">Order By Location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />

  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';
import Job from './types/Job'
import JobList from './components/JobsList.vue'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    //   const state = reactive({
    //     name: 'Link',
    //     age: 25 as number | string
    //   })
    //   state.name = 'Link'
    //   state.age = '25'
    //   return{...toRefs(state)}

    // const name = ref('link')
    // const age = ref<string | number>(25)

    // return { name, age}
    // },

    //   methods: {
    //     changeName(name: string) {
    //       this.name = name
    //       return name
    //     },
    //     changeAge(age: string | number) {
    //       this.age = age
    //       return age
    //   },

    const jobs = ref<Job[]>([
      { title: 'Front-End', location: 'Progressive', salary: 30000, id: '1' },
      { title: 'Back-End', location: 'DST', salary: 50000, id: '2' },
      { title: 'Technician', location: 'Livewire', salary: 20000, id: '3' },
      { title: 'Networking', location: 'Kindi', salary: 10000, id: '4' },
      { title: 'Graphic-Design', location: 'Supersquad', salary: 5000, id: '5' },
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick, order }
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

header .title {
  display: flex;
  justify-content: center;
}

header h1 {
  font-size: 3em;
}
</style>
