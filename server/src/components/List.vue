<template>
    <div id="app">
        <h2>TODO List</h2>

        <form v-on:submit.prevent>
            <input type="text" v-model="newItem">
            <button v-on:click="addItem">Add</button>
        </form>

        <table>
            <tr v-for="(todo, key) in todos" :key="key">
                <td><input type="checkbox" v-model="todo.isDone"></td>
                <td><span v-bind:class="{done: todo.isDone}">{{todo.item}}</span></td>
                <td><button v-on:click="deleteItem(key)">Delete</button></td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
  data () {
    return {
      newItem: '',
      todos: []
    }
  },
  methods: {
    addItem: function (event) {
      if (this.newItem === '') {
        return
      }
      var todo = {
        item: this.newItem,
        isDone: false
      }
      this.todos.push(todo)
      this.newItem = ''
    },
    deleteItem: function (key) {
      this.todos.splice(key, 1)
    }
  }
}
</script>

<style>
  #app table{
    margin-left: auto;
    margin-right: auto;
    text-align: left;
  }
  #app span.done{
    text-decoration:line-through;
  }
</style>