<template>
  <div class="todo-input">
    <input
      :value="value"
      class="todo-input__textfield"
      type="text"
      placeholder="Add to Do"
      @input="handleInput"
    >
    <!-- @input="$emit('input',$event.target.value)" -->
    <button class="todo-input__button" type="submit" @click="handleClick">Create</button>
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
    },

    handleClick(event) {
      this.$emit("create", event);
    }
  }
};
</script>

<style lang="scss">
.todo-input {
  display: flex;
  align-items: center;
  width: 100%;
  border: 1px solid rgba(black, 0.51);
  border-radius: 10px;
  padding: 0 15px;
  &__textfield {
    width: 100%;
    padding: 15px 0;
    margin-right: 15px;
    font-size: 14px;
    border: 0;
    outline: 0;
  }
  &__button {
    -webkit-appearance: none;
    border: 0;
    border-radius: 30px;
    background-color: royalblue;
    color: white;
    padding: 7.5px 15px;
    text-transform: uppercase;
    font-size: 12px;
    outline: 0;
    &:hover {
      cursor: pointer;
      opacity: 0.7;
    }
  }
}
</style>
