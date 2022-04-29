<template>
  <div class="conatainer">
    <AddTask :tasks="tasks" @addNewTask="addNewTask($event)" />
    <div class="body">
      <LoadingTask
        :loadingTask="loadingTasks"
        @romoveLoading="changeStatus($event)"
        @delTask="delTask($event)"
      />
      <DoneTask
        :doneTask="doneTask"
        @romoveDone="changeStatus($event)"
        @delTask="delTask($event)"
      />
    </div>
  </div>
</template>

<script>
import AddTask from "./AddTask.vue";
import DoneTask from "./DoneTask.vue";
import LoadingTask from "./LoadingTask.vue";
export default {
  components: { AddTask, LoadingTask, DoneTask },
  props: ["tasks"],
  computed: {
    loadingTasks() {
      return this.tasks.filter((t) => t.done === false);
    },
    doneTask() {
      return this.tasks.filter((t) => t.done === true);
    },
  },
  methods: {
    changeStatus(e) {
      let ct = [...this.tasks];
      let index = ct.findIndex((t) => t.id === e);
      ct[index].done = !ct[index].done;
      this.$emit("updateTask", ct);
    },
    delTask(e) {
      let ct = [...this.tasks];
      ct = ct.filter((t) => t.id !== e);
      this.$emit("updateTask", ct);
    },
    addNewTask(e) {
      this.$emit("updateTask", e);
    },
  },
};
</script>

<style>
</style>