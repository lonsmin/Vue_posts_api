<template>
    <form @submit.prevent="onSubmit" class="add-form">
        <input type="text" v-model="title" placeholder="Add Task">
        <input type="submit" value="Save Task" class="btn" />
    </form>  
</template>
<script>
export default {
    name:'AddTask',
    data() {
        return {
            id: '',
            title: '',
        }
    }, 
    methods:{
        onSubmit(){                     
            if(!this.title){
                alert('Please add text')
                return
            }
            
            const newTask = {
                title: this.title,
            }
            this.$emit('add-task',newTask)
            this.title = ''
        }
    }
}
</script>
<style scoped>
.btn{
    background: #34495e;
}
.add-form {
  margin-bottom: 40px;
}
input {
  width: 100%;
  height: 40px;
  margin:5px 0;
  padding:0 5px;
  font-size: 17px;
}
</style>