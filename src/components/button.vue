<template>
<button :style="{background:bgcolor,color:'white',padding:'.5em',border:'none'}" > {{text}}</button>   
</template>
<script>
export default{
   name:'Button',
   props:{
      text:String,
      bgcolor:String
   }
}
</script>
<style scoped>



</style>