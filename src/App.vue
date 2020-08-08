<template>
  <div id="app">
    <div v-if="questions[ix].correct - 1 == selected" class="result">
      <div>
        <span style="font-size: 90px; margin: auto;">🎉</span>
        <h3 style="color: #B98744; font-size: 32px;">{{rStatement}}</h3>
      </div>
    </div>
    <div class="body">
      <h5>Question of the day</h5>
      <h2 class="question">{{questions[ix].q}}</h2>
      <div class="answers">
        <div v-for="(ans, i) in questions[ix].answers" 
             @click="selection(i)" 
             class="ans"
             :class="{
                selected: selected == i, 
                right: selected == i && questions[ix].correct - 1 == i,
                wrong: selected == i && questions[ix].correct - 1 != i
                }"
             :key="ans">
          <div class="num">
            <span>{{alphabets[i]}}</span>
          </div>
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
      selected: null,
      rStatement: 'You are right!',
      alphabets: ['A', 'B', 'C', 'D', 'E', 'F', 'G'],
      questions: [{
        q: 'How much wood can a woodchuck chuck?',
        answers: ['200 kg', 'A ton', '200 tons', 'Depends on it\'s size'],
        correct: 4
      }, {
        q: 'New thang',
        answers: ['a', 'b', 'c', 'd'],
        correct: 'a'
      }]
    }
  },
  methods: {
    selection: function (i) {
      var statements = ['You are right!', 'Absolutely right!', 'Correctomundo!']
      var randIx = Math.floor(Math.random() * statements.length)
      this.rStatement = statements[randIx]
      this.selected = i
      return statements[randIx]
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
  background: #B98744;
  top: 0px;
  left: 0px;
}

* {
  font-family: 'Open Sans', Roboto, sans-serif;
}

h5 {
  text-align: center;
  text-transform: uppercase;
  color: hsla(0,0%,100%,.6);
  font-weight: 400;
  letter-spacing: 1px;
}

.result {
  position: fixed;
  width: 100%;
  height: 100%;
  display: flex;
  background: rgb(255, 255, 255);
  z-index: 20;
  animation: show 2s;
  opacity: 0;
  z-index: -1
}

.result div {
  margin: auto;
  display: flex;
  flex-direction: column;
}

@keyframes show {
  0% {
    opacity: 0;
    z-index: 0;
    transform: scale(0);
  }
  30% {
    opacity: 1;
    z-index: 20;
    transform: scale(1);
  }
  80% {
    opacity: 1;
    z-index:20;
  }
  100% {
    z-index: -1;
  }
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

#app h5 {
  text-align: center;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.6)
}

.num {
  width: 40px;
  height: 100%;
  display: flex;
  left: 0px;
  top: 0px;
  border-right: 1px solid rgba(255, 255, 255, 0.6);
  background:rgba(255, 255, 255, 0.6);
}

.num span {
  margin: auto;
  color: #333;
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
  border-radius: 2px;
  border: 1px solid #fff;
  display: flex;
  margin: 8px;
  cursor: pointer;
  color: white;
  position: relative;
}

.ans.selected.right .num span {
  color: teal;
  font-weight: bold;
}
.ans.selected.right {
  color: teal;
} 

.ans.selected.wrong .num span {
  color: tomato;
  font-weight: bold;
}
.ans.selected.wrong {
  color: tomato;
} 

.ans:hover {
  background: rgba(255,255,255,0.4);
}

.ans:active, .ans.selected {
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
  font-weight: 600;
}
</style>
