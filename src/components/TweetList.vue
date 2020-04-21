<template lang="html">
  <div>
    <img :src="tweet.img">
    <p>{{tweet.name}}</p>
    <p>{{tweet.handle}}</p>
    <p>{{tweet.tweet}}</p>
    <p>{{tweet.likes}}</p>
    <br>
  </div>
</template>

<script>
export default {
  name: 'tweet-list',
  props: ['tweet']
  }
</script>

<style lang="css" scoped>
</style>
