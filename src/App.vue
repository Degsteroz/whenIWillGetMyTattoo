<template>
  <div id="app">
    <Main class="main" :msg="messageFromPasha" />
    <div class="form">
      Паша, мы сегодня бьёмся?
      <button ref="button" v-on:click="getAnswer">Узнать</button>
    </div>
  </div>
</template>

<script>
import Main from "./components/main.vue";

export default {
  name: "App",
  components: {
    Main
  },
  beforeMount() { document.title = 'Когда будет рукав?' },
  data: function() {
    return {
      msgList: [
        "Я заболел",
        "Я проткнул палец",
        "Ветром унесло окна на балконе",
        "Я понёс кота в ветеринарку",
        "Я не купил краску",
        "Давай на следующей неделе?"
      ],
      currentIndex: 0
    };
  },

  computed: {
    messageFromPasha: function() {
      return this.msgList[this.currentIndex]
    }
  },
  methods: {
    getAnswer: function() {
      const message = document.getElementById('message')
      message.style.display = 'none'
      this.currentIndex = Math.floor(Math.random() * Math.floor(this.msgList.length))
      setTimeout(function() {
        message.style.display = 'flex'
      }, 10)
    }
  }
};
</script>

<style>
:root {
  --background: #E5FFB3;
  --background-accent: #DBF8A3;
  --background-accent-2: #BDE66E;
  --light: #005bff;
  --dark: #030340;
  --text: #acc7f3;
}

body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-image: url(assets/background.jpg);
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  width: 800px;
  padding: 10px 0;
  background-color: #00ffff;
  border-radius: 10px;

  font-size: 50px;
  margin-left: 50px;
}
button {
  display: block;
  cursor: pointer;
  outline: none;
  border: none;
  background-color: var(--light);
  width: 400px;
  height: 70px;
  border-radius: 30px;
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text);
  background-size: 100% 100%;
  box-shadow: 0 0 0 7px var(--light) inset;
  margin-bottom: 15px;
}

button:hover {
  background-image: linear-gradient(
    145deg,
    transparent 10%,
    var(--dark) 10% 20%,
    transparent 20% 30%,
    var(--dark) 30% 40%,
    transparent 40% 50%,
    var(--dark) 50% 60%,
    transparent 60% 70%,
    var(--dark) 70% 80%,
    transparent 80% 90%,
    var(--dark) 90% 100%
  );
  animation: background 3s linear infinite;
}

@keyframes background {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 400px 0;
  }
}
</style>
