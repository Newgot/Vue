<template>
  <input
      @input="updateInput"
      class="input"
      type="text"
      placeholder="Название"
  />
</template>

<script>
export default {
  name: 'my-input',
  methods: {
    updateInput(event) {
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
</style>