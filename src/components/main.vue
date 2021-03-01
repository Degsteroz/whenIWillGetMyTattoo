<template>
  <div class="main">
    <img class="pasha" src="../assets/pasha.jpg" />
    <div class="bubble_wrapper">
      <span class="text" id="message">{{ msg }}</span>
      <img class="bubble" src="../assets/bubble.png" />
    </div>
  </div>
</template>

<script>
export default {
  name: "main",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  display: flex;
  align-items: center;
}

.pasha {
  width: auto;
  height: 800px;
}

.bubble_wrapper {
  position: absolute;
  width: 20vw;
  height: 30vh;
  left: 345px;
  top: 90px;
  display: flex;
  justify-content: center;
}
.text {
  margin: 20% 0 0 0;
  z-index: 3;
  font-size: 24px;
  max-width: 70%;
  text-align: center;
  animation-duration: 0.3s;
  animation-name: appear;
}
@keyframes appear {
  from {
    margin-top: 10%;
  }
  to {
    margin-top: 20%;
  }
}

.bubble {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 0;
}
</style>
