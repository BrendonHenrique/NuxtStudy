<template>
  <form @submit.prevent="onSubmit">
    <input v-model="text" placeholder="Search joke">
    <button type="submit" class="search-button">Search</button>
  </form>
</template>

<script>
export default {
  name: 'SearchJokes',
  data() { 
    return  { 
      text: '',
    }
  },
  methods: { 
    onSubmit() {
      if(this.text){
        this.$emit('search-text', this.text);
        this.text = '';
      }
    }
  }
}
</script>

<style>
.search-button { 
  display:inline-block;
  padding:0.05em 1.2em;
  border:0.1em solid #000000;
  margin:0 0.3em 0.3em 0;
  border-radius:0.12em;
  box-sizing: border-box;
  color:#000000;
  text-align:center;
  transition: all 0.2s;
}

.search-button:hover{
  color:#FFFFFF;
  background-color:#000000;
}

</style>