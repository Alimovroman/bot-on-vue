<template>
  <div class="root">
    <div><button v-on:click="onShowMessagePizza">пицца</button></div>
    <div><button v-on:click="onShowMessageWeather">будильник</button></div>
    <div><button v-on:click="onShowMessageClock">погода</button></div>

    <div v-if="isShowMessagePizza">
      Хорошо, я закажу пиццу, что еще мне сделать?
    </div>
    <div v-if="isShowMessageWeather">
      Хорошо, погода отличная, что еще мне сделать?
    </div>
    <div v-if="isShowMessageClock">
      Хорошо, будильник установлен, что еще мне сделать?
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowMessagePizza: false,
      isShowMessageWeather: false,
      isShowMessageClock: false,
    };
  },
  methods: {
    onShowMessagePizza() {
      this.isShowMessagePizza = true;
    },
    onShowMessageWeather() {
      this.isShowMessageWeather = true;
    },
    onShowMessageClock() {
      this.isShowMessageClock = true;
    },
  },
  name: "MainPage",
};
</script>

<style>
.root {
  display: flex;
}
</style>
