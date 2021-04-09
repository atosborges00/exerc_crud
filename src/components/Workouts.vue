<template>
    <div :key='workout.id' v-for="workout in workouts">
        <Workout :workout='workout'/>
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
    }
}
</script>