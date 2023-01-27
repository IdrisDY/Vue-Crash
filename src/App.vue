<template>
  <div>
  <Header title="Task Tracker" />
  <Tasks :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/tasks.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return {
      tasks:[]
    }
  },
  created() {
      this.tasks = [{
id:1,
text:'Consultant Ward Round',
day:'March 2nd at 2:30pm',
reminder:true
      },
      {
id:2,
text:'Repute Meeting',
day:'April 1st at 3:15pm',
reminder:true
      },
      {
id:3,
text:'Call Muiz',
day:'December 30 at 7am',
reminder:false
      }]
    }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
