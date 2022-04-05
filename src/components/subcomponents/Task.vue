<template>
    <div class="task">
        
        <h3>{{task.id}}</h3>
        <p>{{task.title}}</p>
        
    </div>
</template>
<script>

export default {
    name: 'Task',
    props: {
        task: Object,
    },
}
</script>
<style scoped>
.task{
    background: #f4f4f4;
    border-radius: 5px;
    margin: 5px;
    padding: 10px 20px;
}
p{
    margin: 5px 0;
}
</style>