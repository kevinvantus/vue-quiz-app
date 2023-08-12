<template>
  <div
    class="callout-ctr is-flex is-align-items-center is-justify-content-center"
    :class="{
      success: status === 'success' || !status,
      error: status === 'error',
    }"
  >
    <ph-check-circle :size="16" weight="fill" v-if="status === 'success'" />
    <ph-x-circle :size="16" weight="fill" v-else />
    <p class="callout-text is-flex-grow-1 has-text-weight-medium">
      {{
        status === "success"
          ? "You passed this quiz successfully."
          : "You failed this quiz, better luck next time."
      }}
    </p>
    <div class="callout-success-rate has-text-weight-medium">
      {{ correct }}/{{ numOfQuestions }}
    </div>
  </div>
</template>

<script>
import { PhCheckCircle, PhXCircle } from "@phosphor-icons/vue";

export default {
  components: {
    PhCheckCircle,
    PhXCircle,
  },
  props: ["status", "correct", "numOfQuestions"],
};
</script>

<style lang="scss" scoped>
.callout-ctr {
  border-radius: 0.5rem;
  padding: 0.625rem 1rem;
  gap: 0.75rem;

  &.success {
    background: rgba(241, 255, 247, 1);
    color: rgba(33, 150, 83, 1);
  }
  &.error {
    background-color: #ffcbcb;
    color: #db3e3e;
  }
  .callout-text {
    line-height: 1.71;
    font-size: 0.875rem;
  }
}
</style>
