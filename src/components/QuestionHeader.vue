<template>
  <header class="question-header">
    <h2 class="has-text-weight-medium is-size-6 is-uppercase">
      Question {{ currentQuestion + 1 }}
    </h2>
  </header>
</template>

<script>
export default {
  props: ["currentQuestion"],
};
</script>

<style lang="scss" scoped>
.question-header {
  background: rgba(238, 238, 238, 1);
  padding: 1rem var(--padding-inline);
  margin-block-end: 0.75rem;
}
</style>
