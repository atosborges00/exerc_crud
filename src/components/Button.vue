<template>
    <button @click="onCLick()" :style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String,
    },
    methods:{
        onCLick(){
            console.log('click')
        }
    }
}
</script>