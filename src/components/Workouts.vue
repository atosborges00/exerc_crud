<template>
    <div :key='workout.id' v-for="workout in workouts">
        <Workout @delete-workout="$emit('delete-workout', workout.id)" :workout='workout'/>
    </div>
</template>

<script>
import Workout from './Workout'

export default {
    name: 'Workouts',
    props: {
        workouts: Array,
    },
    components:{
        Workout
    },
    emits: ['delete-workout'],
}
</script>