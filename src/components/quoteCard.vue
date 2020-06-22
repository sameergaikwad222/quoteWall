<template>
  <div>
    <h1>{{Quote.text}}</h1>
    <p style="font-family: Avenir, Helvetica, Arial, sans-serif;"><strong>-- {{Quote.author}}</strong></p>
  </div>
</template>

<script>
export default {
  props: {
    Quote: Object
  },
};
</script>

<style scoped>
  p{
    margin-left: 50%;
  }
</style>>

