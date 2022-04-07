<template>
<div>
    <div v-for="task in tasks" :key="task.id">
        <Task :task="task" @delTask="$emit('delTask',$event)"/>
    </div>
</div>    
</template>
<script>
import Task from './subcomponents/Task.vue'

export default {
    name:'Tasks',

    props: {
        tasks: Array,
    },
    components: {
        Task
    },
    
}
</script>
<style>

</style>