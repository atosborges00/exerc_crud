<template>
    <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Workout</label>
      <input type="text" v-model="text" name="text" placeholder="Add Workout" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control">
      <label>Time Spent</label>
      <input
        type="text"
        v-model="time"
        name="time"
        placeholder="Add Time Spent"
      />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
    name:'AddWorkout',
    data(){
        return{
            text: '',
            day: '',
            time: '',
        }
    },
    methods: {
        onSubmit(e){
            e.preventDefault();

            if(!this.text){
                alert('Please add a workout')
                return
            }

            const newWorkout= {
                id: Math.floor(Math.random()*100000),
                text: this.text,
                day: this.day,
                time: this.time
            }

            this.$emit('add-workout', newWorkout)

            this.text = ''
            this.day = ''
            this.time = ''
        }
    }
}
</script>


<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>