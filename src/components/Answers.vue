<template>
  <ul class="has-text-weight-medium">
    <li
      class="answer is-flex is-align-items-center"
      v-for="(answer, j) in answers"
      :key="answer"
      @click="selectAnswer(j)"
      :class="{
        correct: correctAnswer === selectedAnswer && correctAnswer === j,
        'gray-out': answerChecked && correctAnswer !== j,
      }"
    >
      <span class="is-flex-grow-1">{{ answer }}</span>
      <span
        class="badge is-size-7 has-text-white has-text-weight-medium"
        v-show="answerChecked && correctAnswer === j"
        >Correct</span
      >
      <ph-radio-button
        size="20"
        color="#219653"
        weight="fill"
        v-if="selectedAnswer !== null && selectedAnswer === j"
      ></ph-radio-button>
      <ph-circle size="20" color="rgba(223, 224, 223, 1)" v-else></ph-circle>
    </li>
  </ul>
</template>

<script>
import { PhCircle, PhRadioButton } from "@phosphor-icons/vue";

export default {
  props: ["answers", "correctAnswer", "selectedAnswer", "answerChecked"],
  components: {
    PhCircle,
    PhRadioButton,
  },
  data() {
    return {};
  },
  methods: {
    selectAnswer(index) {
      this.$emit("select-answer", index);
    },
  },
  emits: ["select-answer"],
};
</script>

<style lang="scss" scoped>
.answer {
  font-size: 1rem;
  line-height: 1.25;
  color: rgba(16, 18, 17, 1);
  border: 0.6px solid rgba(223, 224, 223, 1);
  border-radius: 12px;
  background: linear-gradient(0deg, #fafafa, #fafafa);
  padding: 1.5rem;
  margin-block-end: 0.5rem;
  cursor: pointer;
  gap: 0.75rem;
  &.correct {
    border-color: rgba(33, 150, 83, 1);
  }
  &.gray-out {
    opacity: 0.6;
    cursor: not-allowed;
  }
  .badge {
    background: rgba(33, 150, 83, 1);
    border-radius: 60px;
    padding: 0.25rem 0.75rem;
  }
}
</style>
