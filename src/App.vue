<template>
  <h1 class="title">
    <strong>tic</strong>-<strong>tac</strong>-<strong>toe</strong>
  </h1>
  <Grid :gameGrid="gameGrid" @click="pressedCell" />
  <Button />
</template>

<script>
import Grid from '@/components/Grid.vue';
import Button from '@/components/Button.vue';

export default {
  name: 'app',
  components: {
    Grid,
    Button,
  },
  data() {
    return {
      gameGrid: [0, 0, 0, 0, 0, 0, 0, 0, 0],
      step: 1,
    };
  },
  methods: {
    pressedCell({ target }) {
      const isTargetClick = target.classList.contains('cell');

      if (isTargetClick) {
        const cellIndex = target.dataset.index;

        this.gameGrid[cellIndex] = this.step;

        if (this.step === 2) {
          this.step = 1;
        } else {
          this.step = 2;
        }
      }
    },
  },
};
</script>

<style lang="scss">
:root {
  --color-player1: hsl(42, 83%, 60%);
  --color-player2: hsl(161, 64%, 71%);
  --color-grid-background: hsl(228, 4%, 52%);
  --color-cell-background: hsl(227, 5%, 38%);

  --color-global-black: hsl(0, 0%, 0%);
  --color-global-white: hsl(0, 0%, 100%);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

.title {
  color: var(--color-grid-background);

  & > strong:nth-child(2n) {
    color: var(--color-player2);
  }
  & > strong:nth-child(2n + 1) {
    color: var(--color-player1);
  }
}
</style>
