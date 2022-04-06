<template>
<div class="container">
  <Header />
  <Tasks :tasks="tasks" />
  <Button color="brown" text="More items..." @click="moreItems()"/>
</div> 
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import Button from './components/subcomponents/Button.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    Button,
  },
  methods:{
    async getTasks(){

      const res = await fetch('https://jsonplaceholder.typicode.com/todos?_page='+this.params.pageNumber+'&_limit='+this.params.limitNumber)
      const data = await res.json();
      return data
    },
    async moreItems(){
      this.params.pageNumber = this.params.pageNumber + 1;
      this.tasks = this.tasks.concat(await this.getTasks())
    }
  },
  computed: {
    
  },
  data() {
    return {
      params:{
        pageNumber: 1,
        limitNumber:5,
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
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
 
}

</style>
