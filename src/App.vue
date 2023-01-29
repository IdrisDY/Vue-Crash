<template>
  <div>
  <AddTask v-if="showAddTask"  @addtask="addTask" />
  <Header title="Task Tracker" @showAddTask="toggleAddTask" :taskFunc="showAddTask" />
  <Tasks @delete-task="deleteTask" :tasks="tasks"  @toggle-task="toggleTask" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/tasks.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks:[],
      showAddTask:false
    }
  },
  methods:{
    async deleteTask(id){
      console.log(id);
      if (confirm('Are you sure?'))
      {
        const resp = await fetch(`http://localhost:5000/tasks/${id}`,
{
  method:'DELETE',
  headers:{
'Content-Type':'application/json'
  }
})
res.status === 200?(this.tasks = this.tasks.filter((task) =>task.id !== id)
):alert('cant load tasks at this time')
      }
    },
   async toggleTask(id)
   {
    const data = await fetch(`http://localhost:5000/tasks/${id}`)
    const taskToggle = await data.json()
    const updTask = {...taskToggle , reminder:!taskToggle.reminder}
    console.log('toggled', taskToggle);


    const res = await fetch(`http://localhost:5000/tasks/${id}`,
{
  method:'PUT',
  headers:{
'Content-Type':'application/json'
  },
  body:JSON.stringify(updTask)
})

const newTask = await res.json()

console.log(newTask);

    this.tasks =this.tasks.map((task)=>{
      if (id === task.id){
        return {...task, reminder:!newTask.reminder}
      }
      return task
    })
    },
   async addTask(task){
const res = await fetch ('http://localhost:5000/tasks',
{
  method:'POST',
  headers:{
'Content-Type':'application/json'
  }
  ,
  body:JSON.stringify(task)
}
)
const data = await res.json()
console.log(data)
this.tasks = [...this.tasks,data]
console.log('pushed to array',this.tasks);
setTimeout(() => {
  this.showAddTask = false

}, 600);
    },
    toggleAddTask(){
      setTimeout(() => {
  this.showAddTask = !this.showAddTask

}, 200);
    },
    async fetchTasks(){
const res = await fetch ('http://localhost:5000/tasks')
const data = await res.json()
return data
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
//       this.tasks = [{
// id:1,
// text:'Consultant Ward Round',
// day:'March 2nd at 2:30pm',
// reminder:true
//       },
//       {
// id:2,
// text:'Repute Meeting',
// day:'April 1st at 3:15pm',
// reminder:true
//       },
//       {
// id:3,
// text:'Call Muiz',
// day:'December 30 at 7am',
// reminder:false
//       }]
    }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
