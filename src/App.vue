<template>
  <div class="container">
    <Header title='Workout Log' />
    <AddWorkout @add-workout="addWorkout" />
    <Workouts @delete-workout="deleteWorkout" :workouts = 'workouts'/>
  </div>
</template>

<script>
import Header from './components/Header'
import Workouts from './components/Workouts'
import AddWorkout from './components/AddWorkout'

export default {
  name: 'App',
  components: {
    Header,
    Workouts,
    AddWorkout,
  },
  data(){
    return{
      workouts: []
    }
  },
  methods: {
    addWorkout(workout){
      this.workouts = [...this.workouts, workout]
    },
    deleteWorkout(id){
      if(confirm('Are you shure?')){
        this.workouts = this.workouts.filter((workout) => workout.id !== id)
      }
    },
    async fetchWorkouts(){
      const res = await fetch('http://localhost:5000/workouts')

      const data = await res.jason()

      return data
    }
  },
  async created(){
    this.workouts = await this.fetchWorkouts()
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
