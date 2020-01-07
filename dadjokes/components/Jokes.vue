<template>
  <nuxt-link :to="`jokes/${id}`">
    <div class="joke">
      <p>{{joke}}</p>
    </div>  
  </nuxt-link>
</template>

<script>
export default {
  name: 'joke',
  props:['joke', 'id']
}
</script>

<style>
  .joke { 
    padding: 1rem;
    border: 1px dotted #ccc;
    margin: 1rem 0;
    cursor: pointer;
    transition: .8s all;
  }
  
  .joke:hover { 
    border-bottom: 0 none;
    border: 1px dotted #ccc;
    box-shadow: 0 1px 5px rgba(0, 0, 0, 0.46);
    transform: scale(1.04);
  }

</style>