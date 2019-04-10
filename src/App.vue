<template>
  <div id="app">
    <!-- <header class="app-header">
      <h1 class="app-header__headline">Text</h1>
    </header>  susikurem componenta appheader, cia ji paimportinam ir pa exportiname-->
    <AppHeader v-bind:date="headerDate">
      <!-- Vietoje v-bind:date, galima rasyti tiesiog :date -->
      <!-- Viskas ka cia rasome, bus pakeista vietoje slot, kuris yra AppHeader
      Toliau reikia tempalet, je keli slotai su savo namais-->
      <!-- <template slot="headline">My Day</template> -->
      <!-- <template slot="subtitle">subtitle</template> -->
      <template>My Day</template>
    </AppHeader>
    <div class="todos">
      <TodoList>
        <!-- Todo item per slota nukeliaus -->
        <TodoItem v-for="(todo,index) in todos" :key="todo + index" :todo="todo" :index="index"/>
      </TodoList>
      <!-- <ul class="todo-list__list">
        <li v-for="(todo,index) in todos" class="todo-list__item" :key="todo + index">#{{index+1}}{{todo.title}}</li>
      </ul>-->
    </div>
    <!-- {{newTodo}} -->
    <TodoInput v-model="newTodo" @create="createTodo"/>
    <!-- @created yra tas pats kaip v-on:creted -->
  </div>
</template>

<script>
import AppHeader from '@/components/AppHeader'
import TodoInput from '@/components/Todoinput'
import TodoItem from '@/components/TodoItem'
import TodoList from '@/components/TodoList'

export default {
  name: 'App',
  components: {
    AppHeader,
    TodoInput,
    TodoItem,
    TodoList
  },
  data: () => ({
    newTodo: null,
    headerDate: new Date('2018 04 09'),
    todos: [] 
  }),
  methods: {
    createTodo () {
      // console.log("works");
      if (this.newTodo !== null && this.newTodo.length > 0) {
        this.todos.push({
          title: this.newTodo,
          done: false
        })
        this.newTodo = null
      }
    }
  }

  // data() {
  //   return {
  //     headerDate: new Date("2018 04 09"),

  //   };
  // }
}
</script>

<style lang="scss">
.todos {
  padding: 30px 15px;
}
</style>
