<template>
  <div id="app">
    <div class="container">
      <Header @toggleAddTask="toggleTaskForm" title="Task Tracker" :showAddTask="showAddTask"/>
      <div v-show="showAddTask">
        <AddTask @add-task="addTask"/>
      </div>
      <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
    </div>
  </div>
</template>

<script>
import Header from './components/header'
import Tasks from './components/Tasks' 
import AddTask from './components/AddTask' 

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    toggleTaskForm() {
      this.showAddTask = !this.showAddTask
    },
    deleteTask(id) {
      if(true/*confirm('Are you sure?')*/) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meeting at School',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00AM',
        reminder: false,
      },
    ]
  },
}
</script>

<style>
  @import './css/index.css';
</style>
