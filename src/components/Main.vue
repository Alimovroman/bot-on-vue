<template>
  <div class="root">
    <div v-if="isFirstLoading" class="loading">...</div>
    <div v-else class="botMessage">Привет! Что я могу для вас сделать?</div>
    <div
      class="messagesWrapper"
      v-for="message in botMessages"
      :key="message.id"
    >
      <div class="botMessage">
        {{ message }}
      </div>
    </div>
    <div class="buttons" v-if="!isLoading && !isFirstLoading">
      <div class="btnWrapper" v-if="!isShowMessagePizza">
        <button v-on:click="onShowMessagePizza" class="btn">
          Заказать пиццу
        </button>
      </div>
      <div class="btnWrapper" v-if="!isShowMessageClock">
        <button v-on:click="onShowMessageClock" class="btn">
          Установить будильник
        </button>
      </div>
      <div class="btnWrapper" v-if="!isShowMessageWeather">
        <button v-on:click="onShowMessageWeather" class="btn">
          Сказать какая погода
        </button>
      </div>
    </div>
    <div v-else-if="isLoading" class="loading">...</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      botMessages: [],
      isShowMessagePizza: false,
      isShowMessageWeather: false,
      isShowMessageClock: false,
      isLoading: false,
      isFirstLoading: true,
    };
  },
  mounted() {
    setTimeout(() => {
      this.isFirstLoading = false;
    }, 1000);
  },
  methods: {
    addMessage(text) {
      this.isLoading = true;
      setTimeout(() => {
        this.botMessages.push(
          `Хорошо, ${text}, ${
            this.botMessages.length === 2
              ? "лимит вопросов исчерпан."
              : "что еще мне сделать?"
          }`
        );
        this.isLoading = false;
      }, 1000);
    },
    onShowMessagePizza() {
      this.addMessage("я закажу пиццу");
      this.isShowMessagePizza = true;
    },
    onShowMessageWeather() {
      this.addMessage("погода отличная");
      this.isShowMessageWeather = true;
    },
    onShowMessageClock() {
      this.addMessage("будильник установлен");
      this.isShowMessageClock = true;
    },
  },
  name: "MainPage",
};
</script>

<style>
.root {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  width: 400px;
  height: 550px;
  background: rgb(211, 236, 236);
  border-radius: 20px;
  padding-top: 20px;
}
.botMessage {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  padding: 10px;
  width: 110px;
  border-radius: 10px;
  border: #7290ac 1px solid;
  align-self: flex-end;
  margin: 10px;
  background: rgb(201, 234, 234);
}
.messagesWrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
}
.buttons {
  display: flex;
}
.btnWrapper {
  display: flex;
  justify-content: center;
  background: #7290ac;
  margin: 4px;
  width: 110px;
  border-radius: 10px;
}
.btn {
  border: none;
  background: inherit;
  color: rgb(211, 236, 236);
  padding: 10px;
  border-radius: 10px;
}
.loading {
  background: #7290ac;
  color: rgb(211, 236, 236);
  font-size: 22px;
  padding: 10px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30px;
  align-self: self-start;
  margin: 10px;
}
</style>
