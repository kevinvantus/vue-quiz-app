<template>
  <div class="callout-ctr is-flex is-align-items-center">
    <ph-check-circle :size="16" weight="fill" />
    <p class="callout-text is-flex-grow-1 has-text-weight-medium">
      You passed this module’s quiz successfully
    </p>
    <div class="callout-success-rate"></div>
  </div>
</template>

<script>
import { PhCheckCircle } from "@phosphor-icons/vue";

export default {
  components: {
    PhCheckCircle,
  },
};
</script>

<style lang="scss" scoped>
.callout-ctr {
  border-radius: 0.5rem;
  background: rgba(241, 255, 247, 1);
  padding: 0.625rem 1rem;
  color: rgba(33, 150, 83, 1);
  margin: 1.5rem 2rem 2rem;
  gap: 0.75rem;

  .callout-text {
    line-height: 1.71;
    font-size: 0.875rem;
  }
}
</style>
