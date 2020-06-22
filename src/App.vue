<template>
  <div id="app">
    <div class="b-container-fluid w-25 m-auto">
      <b-card>
        <b-card-text>
          <transition name="slide-fade">
            <quoteCard :Quote="this.currentQuote" v-if="show" />
          </transition>
        </b-card-text>
        <b-button
          @click="getlatestQuote"
          variant="primary"
          style="font-family: Avenir, Helvetica, Arial, sans-serif;"
        >Next Quote</b-button>
      </b-card>
    </div>
  </div>
</template>

<script>
import quoteCard from "./components/quoteCard.vue";
import quotes from "@/data/quotes.js";
export default {
  name: "App",
  data: function() {
    return {
      random: 0,
      currentQuote: quotes[this.random],
      show: true
    };
  },
  components: {
    quoteCard
  },
  methods: {
    getlatestQuote() {
      this.show = false;
      var num = Math.floor(Math.random() * quotes.length);
      this.currentQuote = quotes[num];
    }
  },
  quotes,
  beforeCreate: function() {
    this.random = Math.floor(Math.random() * quotes.length);
  },
  updated: function() {
    this.show = true;
  }
};
</script>

<style>
#app {
  font-family: "Piedra", cursive;
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
