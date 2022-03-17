<script >
export default {
  el: '#app',

  data() {
    return {
      isEditing: false,
      todo: '',
      todos: [],
      selectedTodo: null
    }
  },

  methods: {
    storeTodo() {
      this.todos.push( this.todo )
      this.todo = ''
    },

    removeTodo( index ) {
      this.todos.splice( index, 1 )
    },

    updateTodo() {
      this.todos.splice( this.selectedIndex, 1, this.todo )
      this.todo = ''
      this.isEditing = false
    },

    editTodo( index, todo ) {
      this.isEditing = true
      this.todo = todo
      this.selectedIndex = index
    }
  }
}

</script>

<template>
  <div id="app" class="container">
    <h1>Todo List</h1>

    <div v-if=" !isEditing ">
      <input type="text" v-model=" todo " />
      <input type="submit" value="Add" @click=" storeTodo " />
    </div>
    <div v-else>
      <input type="text" v-model=" todo " />
      <input type="submit" value="Update" @click=" updateTodo " />
    </div>

    <ol>
      <li v-for="(     todo, index     ) in      todos     " :key=" index ">
        {{ todo }}
        <button @click=" editTodo( index, todo ) ">Edit</button>
        <button @click=" removeTodo( index ) ">Delete</button>
      </li>
    </ol>
  </div>
</template>

<style>
</style>
