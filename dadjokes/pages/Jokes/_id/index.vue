<template>
  <div>
    <h3>Single Joke</h3>
    <br>
    <p>
      {{joke}}
    </p>
  </div>  
</template>

<script>
import axios from 'axios';

export default {
  data() { 
    return  { 
      joke: {}  
    }
  },  
  async created() {
    const config = { 
      headers: { 
        'Accept': 'Application/Json',
      }
    }
    try { 
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
      this.joke = res.data.joke;
      console.log(this.joke);
    } catch(error) { 
      console.log(error);
    }
  },  
  head() {
    return {
      title: this.joke,
      meta: [ 
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  },
}
</script>
