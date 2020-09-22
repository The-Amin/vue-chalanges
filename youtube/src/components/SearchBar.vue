<template>
  <div>
    <input @input="onInput" type="text" name="" id="" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  computed: {},
  methods: {
    onInput: function(event) {
      this.$emit('newSearch', event.target.value);
    }
  }
};
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 45px;
}
</style>
