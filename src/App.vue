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
    <div class="todo-list">
      <ul class="todo-list__list"></ul>
    </div>
    {{newTodo}}
    <TodoInput v-model="newTodo"/>
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader";
import TodoInput from "@/components/Todoinput";

export default {
  name: "App",
  components: {
    AppHeader,
    TodoInput
  },
  data: () => ({
    newTodo: "null",
    headerDate: new Date("2018 04 09")
  })

  // data() {
  //   return {
  //     headerDate: new Date("2018 04 09"),

  //   };
  //}
};
</script>

<style lang="scss">
.todo-list {
  padding: 30px 15px;

  &__list {
    list-style: none;
    margin: 0;
    padding: 0;
  }
}
</style> 