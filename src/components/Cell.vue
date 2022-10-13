<template>
  <div class="cell">{{ cellValue }}</div>
</template>

<script>
export default {
  name: 'c-cell',
  props: {
    cellValue: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style lang="scss" scoped></style>
