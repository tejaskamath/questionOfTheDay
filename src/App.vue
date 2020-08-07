<template>
  <div id="app">
    <div class="body">
      <h2 class="question">{{questions[0].q}}</h2>
      <div class="answers">
        <div class="ans" v-for="ans in questions[0].answers" :key="ans">
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
      questions: [{
        q: 'How much wood can a woodchuck chuck?',
        answers: ['a', 'b', 'c', 'd'],
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
}

.answers {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
  flex-wrap: wrap;
}

.ans {
  min-width: 15%;
  height: 40px;
  border-radius: 2px;
  border: 1px solid #aaa;
  display: flex;
  margin: 8px;
  cursor: pointer;
}

.ans:hover {
  background: #f5f5f5;
}

.ans:active {
  background: #eee;
}

@media (max-width: 768px) {
  .ans {
    width: 100%;
  }
}

.ans p {
  margin: auto;
  font-size: 20px;
}
</style>
