<template lang="html">
  <div id="app">
    <h1>The total of likes of the below tweets are {{totalLikes}}!</h1>
    <h1>This is a list of tweets</h1>
    <tweet-list v-for="(tweet, index) in filteredUsers" :key="index" :tweet="tweet"></tweet-list>

    <form v-on:submit.prevent="saveTweet">
      <h3>Add a new tweet</h3>
      <input type="text" placeholder="Name" v-model="newTweetItem.name"/>
      <input type="text" placeholder="Handle" v-model="newTweetItem.handle"/>
      <input type="text" placeholder="Tweet" v-model="newTweetItem.tweet"/>
      <input type="number" v-model.number="newTweetItem.likes">
      <input type="submit" value="save tweet">
    </form>

    <div id="filterInput">
      <h3>Filter user by tweets</h3>
      <input type="number" v-model.number="filterAmount">
    </div>

  </div>
</template>

<script>
import TweetList from './components/TweetList.vue'
export default {
  name: 'app',
  data() {
    return {
      tweets: [
        {
          id: 1,
          name: 'James',
          handle: '@jokerjames',
          img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
          tweet: "If you don't succeed, dust yourself off and try again.",
          likes: 10
        },
        {
          id: 2,
          name: 'Fatima',
          handle: '@fantasticfatima',
          img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
          tweet: 'Better late than never but never late is better',
          likes: 12
        },
        {
          id: 3,
          name: 'Xin',
          handle: '@xeroxin',
          img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
          tweet: 'Beauty in the struggle, ugliness in the success',
          likes: 18
        }
      ],
      newTweetItem: {
        name: "",
        handle: "",
        img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
        tweet: "",
        likes: 0
      },
      filterAmount: 0
    }
  },
  components: {
    'tweet-list': TweetList
  },
  computed: {
    totalLikes: function() {
      return this.tweets.reduce((total, tweet) => total + tweet.likes, 0);
    },
    filteredUsers: function() {
      return this.tweets.filter((tweet) => {
        return tweet.likes >= this.filterAmount
      })
    }

  },
  methods: {
    saveTweet: function() {
      this.tweets.push(this.newTweetItem);

      this.newTweetItem = {
        name: "",
        handle: "",
        tweet: "",
        likes: 0
      };
    }
  }
}
</script>

<style lang="css" scoped>
</style>
