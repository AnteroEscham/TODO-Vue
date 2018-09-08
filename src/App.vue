<template>
  <div id="app">
    <div class="wrapper">
        <div class="container">
          <div class="todo">
            <span class="todo__logo">Todo</span>
            <Todo
              v-for="(type, index) in types"
              :key="index"
              :class="type.modClass"
              :todo="getTodoByType(type.name)"
              :type="type.name"
            />
          </div>
        </div>
    </div>
  </div>
</template>

<script>

import Todo from './components/Todo.vue';
import Header from './components/Header.vue';

export default {
  name: 'app',

  components: {
    Todo,
    Header
  },

  data() {
    return {

      types: [

      {name: 'important', modClass: 'todo__block--red'},
      {name: 'usual', modClass: 'todo__block--green'},
      {name: 'secondary', modClass: 'todo__block--blue'}

      ]

    }
  },
  
  computed: {
    todos() {
      return this.$store.getters.todos;
    }
  },

  methods: {
    getTodoByType(type) {
        return this.todos.filter(elem => elem.type == type);
      }
  }
}

</script>

