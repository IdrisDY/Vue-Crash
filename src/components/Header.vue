<template>
   
   <header>
     {{title}}
     <Button @click = 'onClick()' text="Add task"  bgcolor="green" />
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
      }
   },
   components:{
      Button
   },
   methods:{
      onClick(){
         console.log('clicked');
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