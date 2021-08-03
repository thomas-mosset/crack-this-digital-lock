<template>
  <div>
    <div class="lock">
        <svg fill="none" viewBox="0 0 24 24" height="48" width="48" xmlns="http://www.w3.org/2000/svg">
            <path xmlns="http://www.w3.org/2000/svg" d="M12 4C13.6477 4 15 5.35228 15 7V10H9V7C9 5.35228 10.3523 4 12 4ZM17 10V7C17 4.24772 14.7523 2 12 2C9.24771 2 7 4.24772 7 7V10H6C4.89543 10 4 10.8954 4 12V20C4 21.1046 4.89543 22 6 22H18C19.1046 22 20 21.1046 20 20V12C20 10.8954 19.1046 10 18 10H17ZM6 12H18V20H6V12Z" fill="#0D0D0D"></path>
        </svg>
    </div>
    <section class="section-lock">
      <div class="digitkey-to-guess-div">
        <input
          type="number"
          class="digitkey digitkey-to-guess"
          id="first-nb-to-guess"
          v-model="firstNbToGuess"
        />
        <input
          type="number"
          class="digitkey digitkey-to-guess"
          id="second-nb-to-guess"
          v-model="secondtNbToGuess"
        />
        <input
          type="number"
          class="digitkey digitkey-to-guess"
          id="thrid-nb-to-guess"
          v-model="thirdNbToGuess"
        />
      </div>
      <div class="btn">
        <button
          class="check-btn"
          id="check-btn"
          type="button"
          @click="checkPassword"
        >Check the result</button>
      </div>
      <div class="results">
        <p
        v-for="msg in msg" :key="msg"
        :class="msg.classToApply"
        >{{ msg.msgName }}</p>
      </div>
    </section>
    <p class="title">A numeric lock has a 3 digit key</p>
    <h2 class="title-hint">Hints</h2>
    <section class="section-hint">
        <div class="single-hint">
            <div class="digitkey-div">
                <p class="digitkey">6</p>
                <p class="digitkey">8</p>
                <p class="digitkey">2</p>
            </div>
            <p class="single-hint-hint">One number is correct and well placed</p>
        </div>
        <div class="single-hint">
            <div class="digitkey-div">
                <p class="digitkey">6</p>
                <p class="digitkey">1</p>
                <p class="digitkey">4</p>
            </div>
            <p class="single-hint-hint">One number is correct but wrongly placed</p>
        </div>
        <div class="single-hint">
            <div class="digitkey-div">
                <p class="digitkey">2</p>
                <p class="digitkey">0</p>
                <p class="digitkey">6</p>
            </div>
            <p class="single-hint-hint">Two numbers are correct but wrongly placed</p>
        </div>
        <div class="single-hint">
            <div class="digitkey-div">
                <p class="digitkey">7</p>
                <p class="digitkey">3</p>
                <p class="digitkey">8</p>
            </div>
            <p class="single-hint-hint">Nothing is correct</p>
        </div>
        <div class="single-hint">
            <div class="digitkey-div">
                <p class="digitkey">7</p>
                <p class="digitkey">8</p>
                <p class="digitkey">0</p>
            </div>
            <p class="single-hint-hint">One number is correct but wrongly placed</p>
        </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'CrackPWD',
  data() {
    return {
      firstNbToGuess: '',
      secondtNbToGuess: '',
      thirdNbToGuess: '',
      firstNbAnswer: '0',
      secondtNbAnswer: '4',
      thirdNbAnswer: '2',
      msg: [],
    };
  },
  methods: {
    checkPassword() {
      // empty the message array
      this.msg = [];

      // Check if first given number is correct
      if (this.firstNbToGuess === this.firstNbAnswer) {
        this.msg.push({
          msgName: 'The first number is correct.',
          classToApply: 'correctAnswer',
        });
      } else if (this.firstNbToGuess === '') {
        this.msg.push({
          msgName: 'The first number must not be empty.',
          classToApply: 'incorrectAnswer',
        });
      } else {
        this.msg.push({
          msgName: 'The first number is incorrect.',
          classToApply: 'incorrectAnswer',
        });
      }

      // Check if second given number is correct
      if (this.secondtNbToGuess === this.secondtNbAnswer) {
        this.msg.push({
          msgName: 'The second number is correct.',
          classToApply: 'correctAnswer',
        });
      } else if (this.secondtNbToGuess === '') {
        this.msg.push({
          msgName: 'The second number must not be empty.',
          classToApply: 'incorrectAnswer',
        });
      } else {
        this.msg.push({
          msgName: 'The second number is incorrect.',
          classToApply: 'incorrectAnswer',
        });
      }

      // Check if third given number is correct
      if (this.thirdNbToGuess === this.thirdNbAnswer) {
        this.msg.push({
          msgName: 'The thrid number is correct.',
          classToApply: 'correctAnswer',
        });
      } else if (this.thirdNbToGuess === '') {
        this.msg.push({
          msgName: 'The thrid number must not be empty.',
          classToApply: 'incorrectAnswer',
        });
      } else {
        this.msg.push({
          msgName: 'The thrid number is incorrect.',
          classToApply: 'incorrectAnswer',
        });
      }

      // Check if every number given is correct
      if (
        (this.firstNbToGuess === this.firstNbAnswer)
        && (this.secondtNbToGuess === this.secondtNbAnswer)
        && (this.thirdNbToGuess === this.thirdNbAnswer)) {
        this.msg.push({
          msgName: 'Congratulation, you cracked the password !',
          classToApply: 'correctAnswer',
        });
      }
    },
  },
};
</script>

<style lang="scss">

.title, .title-hint {
  text-align: center;
}

.title-hint {
  text-transform: uppercase;
  margin-top: 5rem;
}

/* section lock */
.section-lock {
  margin-bottom: 1.3rem;
}

.lock, .btn {
  text-align: center;
  margin: 1rem;
}

.digitkey-to-guess-div {
  width: 100%;
  display: flex;
  justify-content: center;
}

.check-btn {
  border: black solid 4px;
  padding: 1rem;
  background-color: #FBFBFB;
  transition: 0.2s;
}

.check-btn:hover {
  cursor: pointer;
  background-color: rgb(231, 229, 229);
}

/* Results */

.results {
  text-align: center;
  padding: 1rem 0;

  &__msg {
    padding: 0.2rem 0;
  }

  p:nth-of-type(4) {
    padding-top: 1rem;
    font-weight: bold;
    font-size: 1.5rem;
    text-transform: uppercase;
  }
}

.correctAnswer {
  color: rgb(0, 158, 13);
}

.incorrectAnswer {
  color: rgb(189, 38, 38);
}

/* digital key */
.digitkey {
  border: black solid 4px;
  width: 2rem;
  height: 2rem;
  padding: 0.5rem;

  display: flex;
  justify-content: center;
  align-items: center;
}

.digitkey-to-guess {
  background-color: #FBFBFB;
}

/* section hint */
.section-hint {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

.single-hint {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 35%;
  margin: 1rem;
}

.single-hint-hint {
  padding-top: 0.5rem;
}

.digitkey-div {
  display: flex;
  justify-content: center;
  width: 100%;
}

</style>
