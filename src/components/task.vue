<template>
   <div @dblclick="$emit('toggle-task',task.id)" :class="[task.reminder?'reminder':'','cont']" >
      <div class="scont" >
         <h3>{{ task.text }}</h3>
      <p>{{ task.day }} </p>
      </div>
      <button @click = 'onDelete(task.id)' > X </button>
   </div>
</template>
<script>
export default {
   name:'Task',
   props:{
task:Object
   },
   methods:{
      onDelete(id){
         // console.log(this.task.id);
         this.$emit('delete-task',id)
      }
   }
}
</script>

<style scoped>

.cont{
   display: flex;
   padding: .5em 1em;
   background: #f4f4f4;
   cursor: pointer;
   margin-top: 1em;
   justify-content: space-between;
   align-items: center;
}
.subcont{
   display: flex;
}
button{
   all: unset;
   color: red;
   font-size: 1.5em;
   font-weight: 900;

}
.reminder{
   border-left: 5px solid green;
}

</style>