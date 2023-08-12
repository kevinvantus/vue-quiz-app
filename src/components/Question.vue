<template>
  <p class="question has-text-weight-normal">
    {{ question }}
  </p>
</template>

<script>
export default {
  props: ["question"],
};
</script>

<style lang="scss" scoped>
.question {
  font-size: 0.875rem;
  line-height: 1.71;
  color: rgba(102, 112, 133, 1);
  margin-block-end: 1.375rem;
}
</style>
