<template>
  <h1 class="title">
    <strong>tic</strong> <strong>tac</strong> <strong>toe</strong>
  </h1>
</template>

<script>
export default {
  name: 'c-title',
};
</script>

<style lang="scss" scoped>
.title {
  align-self: center;
  margin: 0;
  padding: 6px 10px;
  border: 2px solid var(--color-cell-background);
  border-radius: 6px;
  box-shadow: 1px 2px 2px inset var(--color-global-black);
  font-size: 2rem;
  text-transform: uppercase;
  user-select: none;

  & > strong:nth-child(2n) {
    color: var(--color-player2);
  }
  & > strong:nth-child(2n + 1) {
    color: var(--color-player1);
  }
}
</style>
