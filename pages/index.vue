<template>
  <Persepective-layout>
    <Tasks :tasks="tasks" @updateTask="updateTask($event)" />
  </Persepective-layout>
</template>

<script>
import Persepective from "~/layouts/Persepective-layout.vue";
import PersepectiveLayout from "~/layouts/Persepective-layout.vue";
export default {
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "task1",
          description: "task1 description",
          done: false,
        },
        {
          id: 2,
          title: "task2",
          description: "task2 description",
          done: true,
        },
        {
          id: 3,
          title: "task3",
          description: "task3 description",
          done: false,
        },
      ],
    };
  },
  watch: {
    tasks() {
      //  console.log(this.tasks)
    },
  },
  methods: {
    updateTask(e) {
      this.tasks = e;
    },
  },
  components: { Persepective, PersepectiveLayout },
};
</script>

<style>
@import "~/assets/style.css";
</style>
