<template>
  <Title />
  <StepBoard :currentStep="step" :isWinner="isEndGame" />
  <Grid :gameGrid="gameGrid" @mousedown="pressedCell" />
  <Button buttonName="reset" @click="resetGame" />
</template>

<script>
import Grid from '@/components/Grid.vue';
import Button from '@/components/Button.vue';
import StepBoard from '@/components/StepBoard.vue';
import Title from '@/components/Title.vue';

export default {
  name: 'app',
  components: {
    Grid,
    Button,
    StepBoard,
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
    checkLine(cellA, cellB, cellC) {
      return (
        this.gameGrid[cellA] === this.step &&
        this.gameGrid[cellB] === this.step &&
        this.gameGrid[cellC] === this.step
      );
    },
    checkWinner() {
      const isWinLineHorUp = this.checkLine(0, 1, 2);
      const isWinLineHorMid = this.checkLine(3, 4, 5);
      const isWinLineHorBot = this.checkLine(6, 7, 8);

      const isWinLineVertLeft = this.checkLine(0, 3, 6);
      const isWinLineVertMid = this.checkLine(1, 4, 7);
      const isWinLineVertRight = this.checkLine(2, 5, 8);

      const isWinLineDiagLR = this.checkLine(0, 4, 8);
      const isWinLineDiagRL = this.checkLine(2, 4, 6);

      const booleanGroup =
        isWinLineHorUp ||
        isWinLineHorMid ||
        isWinLineHorBot ||
        isWinLineVertLeft ||
        isWinLineVertMid ||
        isWinLineVertRight ||
        isWinLineDiagLR ||
        isWinLineDiagRL;

      if (booleanGroup) {
        this.isEndGame = true;
      } else {
        this.nextStep();
      }
    },
    nextStep() {
      if (this.step === 2) {
        this.step = 1;
      } else {
        this.step = 2;
      }
    },
    pressedCell(event) {
      const isLeftClickMouse = event.button === 0;
      const isTargetClick = event.target.classList.contains('cell');
      const isVisitedCell = !event.target.classList.contains('active');

      const booleanGroup =
        !this.isEndGame && isLeftClickMouse && isTargetClick && isVisitedCell;

      if (booleanGroup) {
        const cellIndex = event.target.dataset.index;
        this.gameGrid[cellIndex] = this.step;

        this.checkWinner();
      }
    },
    resetGame() {
      this.gameGrid = [0, 0, 0, 0, 0, 0, 0, 0, 0];
      this.step = 1;
      this.isEndGame = false;
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
  justify-content: center;
  margin-top: 50px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
