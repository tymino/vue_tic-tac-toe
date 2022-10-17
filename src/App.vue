<template>
  <Title />
  <Grid :gameGrid="gameGrid" @mousedown="pressedCell" />
  <Button buttonName="reset" @click="resetGame" />
</template>

<script>
import Grid from '@/components/Grid.vue';
import Button from '@/components/Button.vue';
import Title from '@/components/Title.vue';

export default {
  name: 'app',
  components: {
    Grid,
    Button,
    Title,
  },
  data() {
    return {
      gameGrid: [0, 0, 0, 0, 0, 0, 0, 0, 0],
      step: 1,
      isEndGame: false,
    };
  },
  methods: {
    pressedCell(event) {
      const isLeftClickMouse = event.button === 0;
      const isTargetClick = event.target.classList.contains('cell');
      const isVisitedCell = !event.target.classList.contains('active');

      const boolGroup =
        !this.isEndGame && isLeftClickMouse && isTargetClick && isVisitedCell;

      if (boolGroup) {
        const cellIndex = event.target.dataset.index;

        this.gameGrid[cellIndex] = this.step;

        if (this.step === 2) {
          this.step = 1;
        } else {
          this.step = 2;
        }
      }
    },
    resetGame() {
      this.gameGrid = [0, 0, 0, 0, 0, 0, 0, 0, 0];
    },
  },
};
</script>

<style lang="scss">
:root {
  --color-player1: hsl(42, 83%, 60%);
  --color-player2: hsl(161, 64%, 71%);
  --color-grid-background: hsl(227, 5%, 38%);
  --color-cell-background: hsl(228, 4%, 52%);

  --color-global-black: hsl(0, 0%, 0%);
  --color-global-white: hsl(0, 0%, 100%);
}

body {
  background: var(--color-grid-background);
}

#app {
  display: flex;
  flex-direction: column;
  margin-top: 50px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
