<template>
  <div class="header">
    <p>Todo List</p>
    <i class="fa-solid fa-plus"></i>
    <img
    @click="addTask"
      class="add-task"
      title="add task"
      src="https://img.icons8.com/external-tanah-basah-detailed-outline-tanah-basah/48/000000/external-plus-user-interface-tanah-basah-detailed-outline-tanah-basah-2.png"
    />
  <AddTaskBox v-if="showBox" :tasks="tasks" @newTask="getTask($event)" @closeBox="closeBox($event)"/>
  </div>
</template>

<script>
import AddTaskBox from "./AddTaskBox.vue";
export default {
    components: { AddTaskBox },
    props: ["tasks"],
    data(){
        return{
            showBox:false
        }
    },
    methods: {
        addTask() {
            this.showBox=true;
        },
        getTask(e){
            let ct=[...this.tasks];
            ct.push(e);
            this.$emit("addNewTask",ct)
            this.showBox=false;
        },
        closeBox(e){
          this.showBox=e
        }
    },
};
</script>

<style>
</style>