<template>
  <section class="quiz">
    <p v-if="!isResult" class="quiz__counter">{{ counter + 1 }}/5</p>
    <h2 v-if="!isResult" class="quiz__title">{{ questions[counter].question }}</h2>
    <div v-show="!isResult" class="quiz__answer" v-for="(answer, index) in questions[counter].answers" :key="index">
      <input class="quiz__radio" type="radio" :id="index" v-model="bufer" :value="index" name="answer">
      <label :for="index">{{ answer }}</label>
    </div>
    <div class="result" v-show="isResult">
      <div>
        <h3 class="result__title">THE NUMBER OF CORRECT ANSWERS: {{  countAns  }}/5</h3>
        <h3 class="result__text">{{ countAns < 2 ? 'IT COULD HAVE BEEN BETTER…' : countAns < 4 ? 'GOOD!' : 'GREAT RESULT!'}}</h3>
      </div>
      <img class="result__img" src="@/assets/card.png" alt="">
    </div>
    <button class="quiz__button" @click="nextQuestion" v-if="counter < 5 && !isResult" :disabled="bufer === null" :class="{ 'quiz__button-disabled' : bufer === null }">{{ counter < 4 ? 'NEXT' : 'RESULT' }}</button>
    <button class="quiz__button" @click="restartQuiz" v-if="isResult">REPEAT</button>
  </section>
</template>

<script>
export default {
  name: 'QuizMy',
  data() {
    return {
      counter:   0,
      countAns:  0,
      correct:   [1, 1, 0, 2, 2],
      bufer:     null,
      isResult:  false,
      questions: [
        {
          question: 'Какое здание является самой высокой исторической постройкой в Праге?',
          answers: [
            'Староместская ратуша',
            'Кафедральный собор Святого Вита',
            'Пражский Град',
            'Танцующий дом'
          ],
        },
        {
          question: 'Какой мост считается одной из главных достопримечательностей Праги и привлекает множество туристов каждый год?',
          answers: [
            'Вышеградский мост',
            'Карлов мост',
            'Новый мост',
            'Малостранский мост'
          ],
        },
        {
          question: 'Какое здание в Праге известно как центр астрономических наблюдений с XV века?',
          answers: [
            'Астрономические часы на Староместской площади',
            'Национальный музей',
            'Клементинум',
            'Обсерватория Жижков'
          ],
        },
        {
          question: 'Какая площадь в Праге знаменита историческими зданиями и крупными событиями?',
          answers: [
            'Карлова площадь',
            'Вацлавская площадь',
            'Площадь Республики',
            'Малостранская площадь'
          ],
        },
        {
          question: 'Какое уникальное архитектурное здание известно как «Танцующий дом»?',
          answers: [
            'Пражский Град',
            'Танцующий дом',
            'Вышеградский замок',
            'Национальный театр'
          ],
        },
      ],
    }
  },
  methods: {
    nextQuestion() {
      if (this.counter < 4) {
        if (this.bufer === this.correct[this.counter]) {
          this.countAns++;
        }
        this.counter++;
        this.bufer = null;
      } else {
        if (this.countAns === this.correct[this.counter]) {
          this.countAns++;
        }
        this.isResult = true;
      }
    },
    restartQuiz() {
      this.counter = 0;
      this.countAns = 0;
      this.bufer = null;
      this.isResult = false;
    }
  }
}
</script>

<style>
  .quiz {
    border-radius: 20px;
    border: 1px solid var(--col5);
    padding: 60px 40px 40px 40px;
    width: 100%; 
  }
  .quiz__title {
    margin: 30px 0px;
  }
  .quiz__answer {
    align-items: center;
    border-bottom: 1px solid var(--col6);
    display: flex;
    padding: 20px;
    gap: 10px;
  }
  .quiz__button {
    margin-top: 4vw;
  }
  .result {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 20px;
  }
  .result__img {
    border-radius: 50%;
  }
  .quiz__radio {
    appearance: none;
    width: 20px;
    height: 20px;
    border: 1px solid var(--col3);
    border-radius: 50%;
    cursor: pointer;
    outline: none;
  }
  .quiz__radio:checked {
    background-color: var(--col4);
    border: none;
  }
  .quiz__radio:checked + label {
    color: red;
  }
  .quiz__button-disabled {
    background: var(--col2);
    cursor: not-allower;
  }
</style>