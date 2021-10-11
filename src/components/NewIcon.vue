<template>
  <div class="n-outer">
    <div :class="['n-veil', 'n-veil-correct', veilCorrect]"></div>
    <div :class="['n-veil', 'n-veil-incorrect', veilIncorrect]"></div>
    <h1>New Icon</h1>
    <div>Please identify the new icons.</div>
    <p>
      Current score: <span class="n-score">{{ score }}</span
      >, correct: {{ correctCount }}, incorrect:
      {{ incorrectCount }}
    </p>
    <div class="n-icon">
      <i :class="['fa', icon]"></i>
    </div>
    <div class="n-space"></div>
    <div class="n-buttons">
      <button @click="buttonClick(false)">Old</button>
      <button @click="buttonClick(true)">New</button>
    </div>
  </div>
</template>

<script>
import FONT_AWESOME_ICONS from '../js/font-awesome-icons.js';
export default {
  name: 'NewIcon',
  data() {
    return {
      ICON_AMOUNT: 120,
      veilCorrect: '',
      veilIncorrect: '',
      correctCount: 0,
      incorrectCount: 0,
      currentIconIndex: 0,
      iconSource: FONT_AWESOME_ICONS.sort(() => Math.random() - 0.5)
        .slice(0, this.ICON_AMOUNT)
        .map((icon, idx) => ({ idx: idx, icon: icon, new: true })),
    };
  },
  computed: {
    score: function () {
      return this.correctCount - this.incorrectCount;
    },
    icon: function () {
      return this.iconSource[this.currentIconIndex].icon;
    },
  },
  methods: {
    buttonClick(isNew) {
      if (isNew === this.iconSource[this.currentIconIndex].new) {
        this.correctCount++;
        this.veilCorrect = 'n-veil-show';
        setTimeout(() => {
          this.veilCorrect = '';
        }, 200);
      } else {
        this.incorrectCount++;
        this.veilIncorrect = 'n-veil-show';
        setTimeout(() => {
          this.veilIncorrect = '';
        }, 200);
      }
      this.iconSource[this.currentIconIndex].new = false;
      this.currentIconIndex =
        Math.trunc(Math.random() * 100000000) % this.ICON_AMOUNT;
    },
  },
};
</script>

<style lang="scss" scoped>
.n-outer {
  display: flex;
  flex-direction: column;
}
.n-veil {
  z-index: -1;
  opacity: 0;
  transition: opacity 0.4s ease-out;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
}
.n-veil-correct {
  background: linear-gradient(
    180deg,
    rgb(16, 255, 16) 0%,
    rgb(255, 255, 255) 50%
  );
}
.n-veil-incorrect {
  background: linear-gradient(
    180deg,
    rgb(204, 0, 0) 0%,
    rgb(255, 255, 255) 50%
  );
}
.n-veil-show {
  opacity: 1;
}
.n-score {
  font-size: 32px;
}
.n-icon {
  align-self: center;
  border: solid 1px #dddddd;
  border-radius: 4px;
  filter: drop-shadow(0px 2px 4px rgba(196, 196, 196, 0.35));
  padding: 24px;
}
i {
  color: #444444;
  font-size: 320px;
}
.n-space {
  align-self: center;
  width: 24px;
  height: 24px;
}
.n-buttons {
  display: flex;
  justify-content: space-between;
}
button {
  flex-grow: 1;
  max-width: 36%;
  padding: 24px;
  font-size: 36px;
}
@media (max-width: 400px) {
  i {
    font-size: 240px;
  }
  button {
    padding: 16px;
    font-size: 28px;
  }
}
</style>
