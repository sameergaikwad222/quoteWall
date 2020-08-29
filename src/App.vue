<template>
  <div id="app">
    <div class="container">
      <div class="row w-100 d-flex flex-row justify-content-center">
        <div
          class="quoteCard-box"
          @click="getlatestQuote"
          v-b-tooltip.focus.rightbottom="{ variant: 'info' }"
          title="Click on Wall"
        >
          <div class="overlay"></div>
          <b-card>
            <b-card-text>
              <transition name="slide-fade">
                <quoteCard :Quote="this.currentQuote" v-if="show" />
              </transition>
            </b-card-text>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import quoteCard from "./components/quoteCard.vue";
import quotes from "@/data/quotes.js";
export default {
  name: "App",
  data: function () {
    return {
      random: 0,
      currentQuote: quotes[this.random],
      show: true,
    };
  },
  components: {
    quoteCard,
  },
  methods: {
    getlatestQuote() {
      this.show = false;
      var num = Math.floor(Math.random() * quotes.length);
      this.currentQuote = quotes[num];
    },
  },
  quotes,
  beforeCreate: function () {
    this.random = Math.floor(Math.random() * quotes.length);
  },
  updated: function () {
    this.show = true;
  },
};
</script>

<style>
#app {
  font-family: "Piedra", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

.quoteCard-box {
  overflow: hidden;
  position: relative;
  box-shadow: 10px 10px 10px #606060;
}

@media only screen and (max-width: 600px) {
  .card {
    width: 100%;
  }
}
.card-body h1,
p {
  color: red;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("./assets/Background.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.5;
  z-index: 1;
  overflow: hidden;
}

body {
  height: 93vh;
  position: relative;
  background-image: linear-gradient(
      135deg,
      transparent 0%,
      transparent 15%,
      rgba(177, 152, 245, 0.5) 15%,
      rgba(177, 152, 245, 0.5) 71%,
      transparent 71%,
      transparent 90%,
      rgba(116, 94, 203, 0.5) 90%,
      rgba(116, 94, 203, 0.5) 100%
    ),
    linear-gradient(
      45deg,
      transparent 0%,
      transparent 47%,
      rgb(177, 152, 245) 47%,
      rgb(177, 152, 245) 58%,
      rgb(137, 114, 217) 58%,
      rgb(137, 114, 217) 80%,
      transparent 80%,
      transparent 100%
    ),
    linear-gradient(90deg, rgb(255, 255, 255), rgb(255, 255, 255));
  background-repeat: no-repeat;
}
</style>
