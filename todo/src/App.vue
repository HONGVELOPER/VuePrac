<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <input 
      type="text" 
      class="w-100 p-2" 
      placeholder= "what i have to do today ? "
      @keyup.enter="addTodo">
    <hr>
    <Todo 
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo"
      @toggle-checkbox="toggleCheckbox"
      @click-delete="deleteTodo" 
    />
    <!-- :todo="todo" 는 todos안에 배열 1개를 todo로 설정한것과 Todo.vue 의 
    props 에 있는 todo와 데이터를 바인딩 시켜주는 역할. -->
  </div>
</template>

<script>
import Todo from "@/components/Todo.vue";
export default {
  components: {
    Todo
  },
  data() {
    return {
      todoText: '',
      todos: [
        { id: 1, text: 'how to use github', checked: false},
        { id: 2, text: 'learning of markdown language', checked: false},
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos.splice(index, 1);
    },
    addTodo(e) {
      this.todos.push({
        id: Math.random(),
        text: e.target.value,
        checked: false     
      });
      this.todoText='';
    },
    toggleCheckbox({id, checked}) {
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos[index].checked = checked;
    }
  }
}
</script>