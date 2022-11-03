<script>
export default {
  data() {
    return {
      inputValue1: '',
      todos: [
        {
          id: 1,
          text: 'But beer 1'
        },
        {
          id: 2,
          text: 'Buy cola 2'
        },
        {
          id: 3,
          text: 'Buy car 3'
        }
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: Date.now(),
        text: this.inputValue1
      })
      this.inputValue1 = ''
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(({id}) => id !== todo.id )
    }
  }
}
</script>

<template>
  <div class="app">
    <form @submit.prevent="addTodo">
      <h3>Создать</h3>
      <input class="input" type="text" :value="inputValue1" @input="inputValue1 = $event.target.value">
      <button class="button">Add todo</button>
    </form>
    <hr style="margin: 10px;">
    <div class="todo" v-for="todo in todos">
      <span>{{todo.text}}</span>
      <button class="button" @click="deleteTodo(todo)">Delete</button>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

.input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid teal;
}

.button { 
  padding: 15px;
  background: none;
  border: 1px solid teal;
  color: teal;
  align-self: flex-end;
}

.todo {
  border: 2px solid teal;
  margin: 15px auto;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

</style>
