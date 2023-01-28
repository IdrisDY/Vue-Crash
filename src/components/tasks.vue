<template>
<div v-for="task in tasks" :key="task.id" >
      <Task @delete-task="$emit('delete-task', task.id)" :task="task"  @toggle-task= "$emit('toggle-task', task.id)" />
   </div>
</template>

<script>
import Task from './task.vue'
export default {
   name:'Tasks',
   props:{
      tasks:Array
   },
   components:{
Task
   },
   emits:['toggle-task']
}
</script>