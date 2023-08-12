<template>
  <div class="question-ctr" v-for="(q, i) in questions" :key="q">
    <transition name="slide" appear mode="in-out">
      <div v-if="currentQuestion === i">
        <question-header :currentQuestion="currentQuestion"></question-header>
        <section class="question-body pb-2">
          <question :question="q.question"></question>
          <answers
            :answers="q.answers"
            :correctAnswer="q.correctAnswer"
            :selectedAnswer="selectedAnswer"
            :answerChecked="answerChecked"
            @select-answer="handleSelectAnswer"
          ></answers>
        </section>
      </div>
    </transition>
  </div>

  <div class="controls mb-5 is-flex is-justify-content-right" v-if="!completed">
    <button
      type="button"
      class="button is-danger has-text-weight-medium is-small"
      @click="currentQuestion = 0"
    >
      Reset Quiz
    </button>
    <button
      type="button"
      class="button is-dark has-text-weight-medium is-small"
      @click="checkAnswer"
      :disabled="selectedAnswer === null"
    >
      Check answer</button
    ><button
      type="button"
      class="button is-success has-text-weight-medium is-small"
      @click="nextClick"
      :disabled="!answerChecked"
    >
      Next
    </button>
  </div>
</template>

<script>
import Answers from "@/components/Answers.vue";
import Question from "@/components/Question.vue";
import QuestionHeader from "@/components/QuestionHeader.vue";

export default {
  components: {
    Answers,
    Question,
    QuestionHeader,
  },
  props: ["questions", "currentQuestion", "totalCorrectAnswers", "completed"],
  data() {
    return {
      answerChecked: false,
      selectedAnswer: null,
    };
  },
  methods: {
    handleSelectAnswer($event) {
      if (this.selectedAnswer !== null) return;
      this.selectedAnswer = $event;
    },
    checkAnswer() {
      const current = this.questions[this.currentQuestion];
      console.log("totalCorrectAnswers:", this.totalCorrectAnswers);
      if (current.correctAnswer === this.selectedAnswer) {
        this.$emit("correct-answer", this.totalCorrectAnswers + 1);
      }
      this.answerChecked = true;
    },
    nextClick() {
      this.answerChecked = false;
      this.selectedAnswer = null;
      this.$emit("next-question");
    },
  },
  emits: ["next-question", "correct-answer"],
};
</script>

<style lang="scss" scoped>
.question-ctr {
  h2 {
    color: rgba(16, 18, 17, 1);
    line-height: 1.25;
  }
  .question-body {
    padding-inline: var(--padding-inline);
  }
}
.controls {
  padding-inline: var(--padding-inline);
  gap: 0.75rem;
}

.slide-enter-from {
  transform: translateX(0);
}
.slide-enter-to {
  transform: translateX(100%);
  transition: all 0.125s;
}

.slide-leave-from {
  transform: translateX(100%);
}

.slide-leave-to {
  transform: translateX(0);
  transition: all 0.125s;
}
</style>
