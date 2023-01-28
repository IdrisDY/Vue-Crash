<template>
   
   <header>
     {{title}}
     <Button @click = 'onClick()' :text= " taskFunc? 'Close' :'Add task' "  :bgcolor=" taskFunc ? 'red' :'green'" />
     <!-- <Button text="Update task" bgcolor="blue" />
     <Button text="Remove task" bgcolor="red" /> -->
   </header>

</template>
<script>
import Button from './button.vue'
export default {
   name:'Header',
   props:{
      title:{
         type:String,
         default:'Hello World'
      },
      taskFunc:  Boolean
   },
   components:{
      Button
   },
   methods:{
      onClick(){
         this.$emit('showAddTask');
      }
   }
}
</script>
<style scoped>
header
{
   color: brown;
   display: flex;
   justify-content: space-between;
}
</style>