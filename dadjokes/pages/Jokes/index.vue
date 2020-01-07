<template>
  <div>
    <Search-joke @search-text="searchText"/>
    <Joke v-for="joke in jokes" :key="joke.id" :joke="joke.joke" :id="joke.id"></Joke>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      jokes : []
    }
  },
  methods: { 
    async searchText(text) { 
      console.log(text)
      const config = { 
        headers: { 
          'Accept': 'Application/Json',
        }
      }

      try { 
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
        console.log(res.data);
        this.jokes = res.data.results;
      } catch(error) { 
        console.log(error);
      }
    }
  },
  async created() {
    const config = { 
      headers: { 
        'Accept': 'Application/Json',
      }
    }
    try { 
      const res = await axios.get("https://icanhazdadjoke.com/search", config);
      console.log(res.data);
      this.jokes = res.data.results;
      console.log(this.jokes)
    } catch(error) { 
      console.log(error);
    }
  }, 
  head(){
    return {
      title: 'Read some dad jokes',
      meta: [ 
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  },
  components: {
    'Joke': require('~/components/Jokes').default,
    'Search-joke': require('~/components/SearchJokes').default,
  }
}
</script>
