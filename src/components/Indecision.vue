<template>
  <h1>Indecision</h1>
  <img v-if="img" :src="img" alt="bg" />
  <div class="bg-dark"></div>
  <div class="indecision-container">
    <input type="text" placeholder="hazme una pregunta" v-model="question" />
    <p>Recuerda termimar con un signo de interrogacion</p>
    <div v-if="isValidQuestion">
      <h2>{{ question }}</h2>
      <h1>{{ answer === "yes" ? "si" : "no" }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: null,
      answer: null,
      img: null,
      isValidQuestion: false,
    };
  },
  methods: {
    async getAnswer() {
      this.answer = "pensando";
      const { answer, image } = await fetch("https://yesno.wtf/api").then(
        (res) => res.json()
      );
      this.answer = answer;
      this.img = image;
    },
  },
  watch: {
    question(value) {
      this.isValidQuestion = false;
      if (!value.includes("?")) return;
      this.isValidQuestion = true;
      this.getAnswer();
    },
  },
};
</script>

<style scoped>
img,
.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  border-radius: 5px;
  border: none;
  padding: 10px 15px;
  width: 250px;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
