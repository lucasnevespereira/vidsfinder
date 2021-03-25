<template>
  <div>
    <input v-on:input=onInput />  
  </div>  
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput: function(e) {
      this.$emit('termChange', e.target.value);
    }
  }
};
</script>

<style>

</style>
