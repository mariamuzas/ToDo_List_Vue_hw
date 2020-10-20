<template>
  <div id="app">
    <h1>{{title}}</h1>
    <form v-on:submit.prevent="saveNewTodo">   
      <label for="todo-input">Add a ToDo:</label>
      <input id="new-item" type="text" v-model="newTodo.name">

      <label for="high">High</label>
      <input type="radio" name="priority" v-model="newTodo.priority" value="high">

      <label for="low">Low</label>
      <input type="radio" name="priority" v-model="newTodo.priority" value="low">

      <input type="submit" value="Save ToDo">
    </form>

    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index" v-bind:class="todo.priority">
        <span>{{todo.name}}</span>
      </li>
    </ul>

  </div>
</template>


<script>
export default {
  data() {
    return {
      title: "ToDo's",
      todos: [
        {name:"Buy shopping", priority: "high"},
        {name:"Clean bathroom", priority: "low"},
        {name:"Car's MOT", priority: "high"}
        ],

      newTodo: {
        name:"",
        priority:""
      }
    }
  },
  methods: {
    saveNewTodo: function() {
      this.todos.push({
        name: this.newTodo.name,
        priority: this.newTodo.priority
        });
      this.newTodo = { 
        name: "",
        priority: ""
      }
    }
  }
}
</script>


<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0 0 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}

li.low {
  border: 2px solid #1a681e;
  color: #1a681e;
}

li.high {
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}
</style>
