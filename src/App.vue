<template>
  <div id="app">
    <button @click="displayNextMessage">Show next</button>
    <transition name="slide-fade" mode="out-in">
      <div :key="seletedMessage">
        {{ seletedMessage }}
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      messages: [
        "Nam non placerat justo, in pulvinar felis. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Morbi vitae facilisis ante. Pellentesque et metus odio. Cras hendrerit eu ex eget fringilla. Vestibulum vestibulum magna a magna sollicitudin lobortis. In non commodo ipsum.",
        "Fusce laoreet quam tempus luctus venenatis. Duis at sodales nulla. Ut porta sodales justo sed blandit. Suspendisse mauris quam, ultricies et ex sed, pellentesque pellentesque mi. Proin nibh augue, pharetra a iaculis eu, pretium quis purus. Curabitur vitae orci enim.",
        "Cras volutpat suscipit rutrum. Proin eget turpis tempus, mattis justo a, porta tellus. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Donec a vestibulum ante, a luctus lectus. Fusce viverra volutpat lorem eu vulputate.",
      ],
      seletedMessage: null,
      messagesIndex: 0,
    };
  },
  mounted() {
    this.seletedMessage = this.messages[0];
  },
  methods: {
    displayNextMessage() {
      if (this.messagesIndex < this.messages.length - 1) {
        this.messagesIndex++;
      } else {
        this.messagesIndex = 0;
      }
      this.seletedMessage = this.messages[this.messagesIndex];
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin: 40px;
}
.slide-fade-enter-active {
  transition: all 0.25s ease;
}

.slide-fade-leave-active {
  transition: all 0.25s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter,
.slide-fade-leave-to {
  transform: scale(0.95);
  opacity: 0;
}

button {
  margin-bottom: 1em;
  background: rgb(41, 41, 41);
  color: #fff;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
}
</style>
