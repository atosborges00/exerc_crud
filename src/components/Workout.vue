<template>
    <div class="workout">
        <h3>
            {{ workout.text }}
            <i @click="$emit('delete-workout', workout.id)" class="fas fa-times"></i>
        </h3>
        <p>{{workout.day}}</p>
        <p>{{workout.time}}:00 h</p>
    </div>
    
</template>

<script>
export default {
    name: 'Workout',
    props: {
        workout: Object
    },
}
</script>

<style scoped>
.fas {
  color: red;
}
.workout {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.workout h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>