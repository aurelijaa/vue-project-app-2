<template>
  <!-- <li :class="['todo-item',{'todo-item--checked':checked}]"> -->
  <li :class="classList">
    <!-- {{checked}} -->
    <div class="todo-item__checkbox">
      <input v-model="checked" type="checkbox">
    </div>
    <div class="todo-item__content">#{{index+1}}.{{todo.title}}</div>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: {
      // type: [Date,String,Number],
      type: Object,
      required: true,
      default: () => ({
        title: null,
        done: false
      })
    },
    index: {
      type: Number,
      default: 0
    }
  },
    data: () => ({
    checked: false
  }),

  computed: {
    classList() {
      const classes = ["todo-item"];
      if (this.checked) {
        classes.push("todo-item__checked");
      }
      return classes;
    }
  }

};
</script>

<style lang="scss">
.todo-item {
  display: flex;
  width: 100%;
  border: 1px solid rgba(black, 0.51);
  border-radius: 10px;
  padding: 15px;
  margin-bottom: 15px;

  &__checkbox {
    margin-right: 15px;
  }
  
  &__checked {
    color: rgba(black, 0.51);
    background-color: whitesmoke;
    text-decoration: line-through;
  }
}
</style>
