<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="clickHandler('title')">order by title</button>
        <button @click="clickHandler('salary')">order by salary</button>
        <button @click="clickHandler('location')">order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "@/types/Job";
import JobList from "@/components/JobList.vue";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    // const state = reactive({name: 'Link', age: 25 as string | number})

    // state.name = 'shaun' // cannot change the type
    // state.age = '37'

    // return {...toRefs(state)}

    // const name = ref('Link')
    // const age = ref<number | string>(25)

    // age.value = 30
    // name.value = 'bilal'

    // return {name, age}

    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 15000,
        id: "1",
      },
      {
        title: "house worker",
        location: "copenhagen",
        salary: 40000,
        id: "2",
      },
      {
        title: "factory worker",
        location: "los vegas",
        salary: 12000,
        id: "3",
      },
      {
        title: "prison worker",
        location: "los angelas",
        salary: 30000,
        id: "4",
      },
    ]);

    const order = ref<OrderTerm>("title");
    const clickHandler = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, clickHandler, order };
  },
  // methods: {
  //   changeName(name: string) {
  //     this.name = name
  //     return name
  //   },
  //   changeAge(age: number | string) {
  //     this.age = age
  //     return age
  //   },
  // }
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
  margin: 0 5px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
