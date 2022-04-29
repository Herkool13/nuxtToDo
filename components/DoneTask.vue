<template>
  <div class="doneTask">
    <div class="done-header">done tasks</div>
    <div class="done-body">
      <div class="task" v-for="(task , index) in doneTask" :key="index">
        <div class="left">
          <img
            class="done-icon"
            @click="removeDone(task.id)"
            src="https://img.icons8.com/external-royyan-wijaya-detailed-outline-royyan-wijaya/24/000000/external-tick-interface-royyan-wijaya-detailed-outline-royyan-wijaya.png"
          />
          <div class="task-box">
            <div class="task-title">{{task.title}}</div>
            <div class="task-description">{{task.description}}</div>
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
    props:['doneTask'],
    methods:{
        removeDone(id){
            this.$emit('romoveDone',id)
        },
        delTask(id){
            this.$emit('delTask',id)
        }
    }
};
</script>

<style>
</style>