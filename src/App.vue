<template>
  <div id="app">
    <addToDo v-on:isApended="addToDo"></addToDo>
    <list :todolist=todolist v-on:isDeleted="deleteItem"></list>
  </div>
</template>

<script>
import addToDo from "./components/addToDo.vue"
import List from "./components/List.vue"

export default {
  name: 'app',
  data () {
    return {
      todolist : [],
      counter : 0,
    }
  },
  mounted(){
    if(localStorage.todolist){
      this.todolist = JSON.parse(localStorage.todolist)
    }
  },
  watch:{
    todolist(newToDo){
      localStorage.todolist = JSON.stringify(newToDo)
    }
  },
  components: {addToDo,List},
  methods : {
    addToDo(todo){
      this.todolist.push({id:this.counter++, data: todo,time:"Added on: "+new Date().toLocaleDateString("tr-TR")+" "+new Date().toLocaleTimeString("tr-TR")})
      console.log(this.todolist)
    },
    deleteItem(id){
      this.todolist = this.todolist.filter(item => item.id != id);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
