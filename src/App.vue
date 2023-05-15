<template>
  <div id="app">
    <AddNewTodo
    @add-new-todo="addNewTodo"
    />
    <ol class="list-group">
      <TodoList
      v-for="(todo, index) in todos" 
      :key="todo.id"
      :index="index"
      :todo="todo"
      @is-checked="isChecked"
      @remove-todo="removeTodo"
      />
    </ol>
  </div>
</template>

<script>
import AddNewTodo from '@/components/AddNewTodo'
import TodoList from "@/components/TodoList.vue"

export default {
  name: 'App',
  components: {
    TodoList, AddNewTodo
  },
  data: () => ({
    todos: [],
    idCounter: 2,
  }),
  methods: {
    isChecked: function(index) {
      this.todos[index].completed = !this.todos[index].completed;
    },
    addNewTodo: function(localInput) {
      this.idCounter++;
      this.todos.push({
        id: this.idCounter,
        title: localInput,
        completed: false,
      })
    },
    removeTodo: function(index) {
      this.todos.splice(index, 1);
    }
  },
  created: function() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(response => response.json())
      .then(data=> this.todos = data)
  }
}
</script>

<style>
#app {
  margin: 20px;
  
}
</style>
