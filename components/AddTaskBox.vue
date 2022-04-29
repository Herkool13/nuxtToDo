<template>
  <div class="add-task-box">
    <h1>add new task</h1>
    <form class="form">
      <input
        class="inp"
        type="text"
        name="title"
        v-model="task.title"
        placeholder="title..."
        required
      />
      <input
        class="inp"
        type="text"
        name="description"
        v-model="task.description"
        placeholder="description..."
        required
      />
      <button class="inp submit" @click.prevent="sendData()">send</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: {
        title: "",
        description: "",
      },
    };
  },
  props: ["tasks"],
  methods: {
    sendData() {
      let createId = true;
      let id;
      while (createId) {
        id = Math.floor(Math.random() * 100000);
        if (!!!this.tasks.find((t) => t.id === id)) break;
      }
      const newTask = {
        id,
        title: this.task.title,
        description: this.task.description,
        done:false
      };
        this.$emit("newTask", newTask);
        this.task.title='';
        this.task.description='';

    },
  },
};
</script>

<style>
</style>