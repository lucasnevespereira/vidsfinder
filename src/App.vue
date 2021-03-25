<template>
  <div>
   Hello from vidsfinder
   <SearchBar v-on:termChange=onTermChange /> 
  </div>  
</template>

<script>
import SearchBar from "./components/SearchBar";
export default {
  name: 'App',
  components: {
    SearchBar
  },
  methods: {
    onTermChange: (searchTerm) => {
      console.log(searchTerm);
    }
  },
};
</script>
