<template>
<div class="container">
  <Header />
  <AddTask @add-task="addTask($event)"/>
  <Tasks :tasks="tasks" @delTask="delTask($event)" />
  <Button color="brown" text="More items..." @click="moreItems()"/>
</div> 
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import Button from './components/subcomponents/Button.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    Button,
    AddTask,
  },
  methods:{
    async getTasks(){ 
      try{   
      const res = await fetch(
        this.params.api+
        this.params.page+
        this.params.pageNumber+
        this.params.limit+
        this.params.limitNumber)
      const data = await res.json();
      return data    
      }
      catch{
        console.log('error')
      }
    },
    async moreItems(){
      this.params.pageNumber = this.params.pageNumber + 1;
      this.tasks = this.tasks.concat(await this.getTasks())
    },
    async addTask(task){
    const res = await fetch(this.params.api,{
                method:'POST',
                headers:{
                    'Accept':'application/json, text/plain, */*',
                    'Content-type':'application/json'
                },
                body:JSON.stringify(
                  task
                  )
            })
    const data = await res.json(); 
    
    this.tasks = [data].concat(this.tasks) 
    },
    async delTask(id){
    const res = await fetch(this.params.api+'/'+id,{
      method:'DELETE'
    })
    
    this.tasks = this.tasks.filter((task)=>{
      return task.id !== id;
    })

    }
  },
  data() {
    return {

      params:{
        api: 'https://jsonplaceholder.typicode.com/todos',
        page: '?_page=',
        limit: '&_limit=',
        pageNumber: 1,
        limitNumber:3,
      },
      tasks: []
    }
  },
  async created() {
    
    this.tasks = await this.getTasks()

    
  }
}
</script>



<style>
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
  border: 1px solid #34495e;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin:5px 0;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
 
}

</style>
