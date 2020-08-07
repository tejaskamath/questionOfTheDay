<template>
  <div id="app">
    <div class="body">
      <h2 class="question">{{questions[ix].q}}</h2>
      <div class="answers">
        <div @click="selected" class="ans" v-for="ans in questions[ix].answers" :key="ans">
          <p>{{ans}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      ix: 0,
      questions: [{
        q: 'How much wood can a woodchuck chuck?',
        answers: ['200 kg', '150 tons', '80 tons', 'Depends on it\'s size'],
        correct: 'c'
      }, {
        q: 'New thang',
        answers: ['a', 'b', 'c', 'd'],
        correct: 'a'
      }]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;600;700;800&display=swap');
#app {
  position: fixed;
  display: flex;
  height: 100%;
  width: 100%;
  background: #8D6235;
  top: 0px;
  left: 0px;
}

* {
  font-family: 'Open Sans', Roboto, sans-serif;
}

#app .body {
  margin: auto;
  width: 100%;
}

#app .question {
  text-align: center;
  font-size: 32px;
  color: white;
}

.answers {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
  flex-wrap: wrap;
  margin-top: 60px;
}

.ans {
  min-width: 20%;
  height: 40px;
  border-radius: 200px;
  border: 2px solid #fff;
  display: flex;
  margin: 8px;
  cursor: pointer;
  color: white;
}

.ans:hover {
  background: rgba(255,255,255,0.4);
}

.ans:active {
  background: rgba(255,255,255,1);
  color: #8D6235;
}

@media (max-width: 1000px) {
  .ans {
    width: calc(50% - 10%);
  }
}

@media (max-width: 600px) {
  .ans {
    width: calc(100% - 20%);
  }
}

.ans p {
  margin: auto;
  font-size: 20px;
}
</style>
