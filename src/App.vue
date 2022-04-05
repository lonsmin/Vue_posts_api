<template>
<div class="container">
  <Header />
  <Tasks :tasks="tasks"/>
</div> 
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
  },
  methods:{
    async getTasks(){
      let start = 10;
      let limit = 10;
      const res = await fetch('https://jsonplaceholder.typicode.com/todos?_start='+start+'&_limit='+limit)
      const data = await res.json();

      return data
    }
  },
  data() {
    return {
      tasks: []
    }
  },
  async created() {
    this.tasks = await this.getTasks()
    
    // [
    //   {
    //     id:1,
    //     title:'Nadpis',
    //     text:'Text'
    //   }
      
    // ]
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
