<template>
  <div class="todo-list__input">
    <input :value="value" class="todo-list__input-textfield" type="text" @input="handleInput">
    <!-- @input="$emit('input',$event.target.value)" -->
    <button class="todo-list__input-button" type="submit">Create</button>
  </div>
</template>

<script>
export default {
  name: "TodoInput",
  props: {
    value: {
      type: String
    }
  },
  methods: {
    handleInput(event) {
      this.$emit("input", event.target.value);
    }
  }
};
</script>

<style lang='scss'>
.todo-list {
  padding: 30px 15px;

  &__list {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  &__item {
    width: 100%;
    border: 1px solid rgba(black, 0.51);
    border-radius: 10px;
    padding: 15px;
  }

  &__input {
    display: flex;
    align-items: center;
    width: 100%;
    border: 1px solid rgba(black, 0.51);
    border-radius: 10px;
    padding: 0 15px;

    &-textfield {
      width: 100%;
      padding: 15px 0;
      margin-right: 15px;
      font-size: 14px;
      border: 0;
      outline: 0;
    }

    &-button {
      -webkit-appearance: none;
      border: 0;
      border-radius: 30px;
      background-color: blue;
      color: white;
      padding: 7.5px 15px;
      text-transform: uppercase;
      font-size: 17px;
      outline: 0;

      &:hover {
        cursor: pointer;
        opacity: 0.7;
      }
    }
  }
}
</style>
