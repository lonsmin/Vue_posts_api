<template>
    <div class="task">
        
        <h3>{{task.id}}</h3>
        <p>{{task.title}}</p>
        <button @click="$emit('delTask',task.id)">del</button>
        
    </div>
</template>
<script>
import Button from '../../../../vue-crash-2021/src/components/Button.vue'

export default {
  components: { 
      Button 
      },
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
    margin:10px 0;
    padding: 10px 20px;
}
p{
    margin: 5px 0;
}
button{
    background: #c0392b;
    border-radius: 5px;
    margin:10px 0;
    padding: 5px 20px;
    color: #f4f4f4;
}
</style>