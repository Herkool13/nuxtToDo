<template>
  <div class="loadingTask">
    <div class="loading-header">loading tasks</div>
    <div class="loading-body">
      <div class="task" v-for="(task, index) in loadingTask" :key="index">
        <div class="left">
          <img
            class="load-icon"
            @click="romoveLoading(task.id)"
            src="https://img.icons8.com/material-outlined/24/000000/recurring-appointment.png"
          />
          <div class="task-box">
            <div class="task-title">{{ task.title }}</div>
            <div class="task-description">{{ task.description }}</div>
          </div>
        </div>
        <img
          class="del-icon"
          @click="delTask(task.id)"
          src="https://img.icons8.com/material-outlined/24/000000/trash--v1.png"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["loadingTask"],
  methods: {
    romoveLoading(id) {
      this.$emit("romoveLoading", id);
    },
    delTask(id) {
      this.$emit("delTask", id);
    }
  },
};
</script>

<style>
</style>