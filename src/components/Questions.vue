<template>
  <div class="question-ctr" v-for="(q, i) in questions" :key="q">
    <template v-if="currentQuestion === i">
      <header class="question-header">
        <h2 class="has-text-weight-medium is-size-6 is-uppercase">
          Question {{ currentQuestion + 1 }}
        </h2>
      </header>
      <section class="question-body pb-2">
        <p class="question has-text-weight-normal">
          {{ q.question }}
        </p>

        <ul class="has-text-weight-medium">
          <li
            class="answer is-flex is-align-items-center"
            v-for="(answer, j) in q.answers"
            :key="answer"
          >
            <span class="is-flex-grow-1">{{ answer }}</span>
            <ph-radio-button
              size="20"
              color="#219653"
              weight="fill"
              v-if="selectedAnswer && selectedAnswer === j"
            ></ph-radio-button>
            <ph-circle
              size="20"
              color="rgba(223, 224, 223, 1)"
              v-else="!selectedAnswer"
            ></ph-circle>
          </li>
        </ul>
      </section>
    </template>
  </div>
</template>

<script>
import { PhCircle, PhRadioButton } from "@phosphor-icons/vue";

export default {
  components: {
    PhCircle,
    PhRadioButton,
  },
  props: ["questions", "currentQuestion"],
  data() {
    return {
      selectedAnswer: null,
    };
  },
};
</script>

<style lang="scss" scoped>
$padding-inline: 2.25rem;
.question-ctr {
  .question-header {
    background: rgba(238, 238, 238, 1);
    padding: 1rem $padding-inline;
    margin-block-end: 0.75rem;
  }

  h2 {
    color: rgba(16, 18, 17, 1);
    line-height: 1.25;
  }

  .question-body {
    padding-inline: $padding-inline;

    .badge {
      background: rgba(33, 150, 83, 1);
      border-radius: 60px;
    }
    .question {
      font-size: 0.875rem;
      line-height: 1.71;
      color: rgba(102, 112, 133, 1);
      margin-block-end: 1.375rem;
    }

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

      &.selected {
        border-color: rgba(33, 150, 83, 1);
      }
    }
  }
}
</style>
