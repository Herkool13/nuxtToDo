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
      <small v-if="task.title.length < 2"
        >title should more than 2 carater</small
      >
      <input
        class="inp"
        type="text"
        name="description"
        v-model="task.description"
        placeholder="description..."
        required
      />
      <small v-if="task.title.length > 70"
        >title should less than 70 carater</small
      >
      <div class="btn-box">
        <button class="inp submit" @click.prevent="sendData()">send</button>
        <button class="inp cancel" @click="cancel()">cancel</button>
      </div>
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
      showBox:false
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
      if (this.task.title.length >= 2 && this.task.description.length <= 70) {
        const newTask = {
          id,
          title: this.task.title,
          description: this.task.description,
          done: false,
        };
        this.$emit("newTask", newTask);
        this.task.title = "";
        this.task.description = "";
      }
    },
    cancel(){
      this.$emit("closeBox",this.showBox)
    }
  },
};
</script>

<style scoped>
small {
  color: rgb(255, 0, 0);
}
.btn-box{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.cancel{
  width: 45%;
  background-color: #fff;
      border: none;
  transition-duration: 600ms;
}
.cancel:hover{
  background-color: yellow;
}
</style>