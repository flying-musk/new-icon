<template>
  <div class="n-outer">
    <h1>New Icon</h1>
    <h2>Please identify the new icons.</h2>
    <p>
      Current score: {{ score }}, correct: {{ correctCount }}, incorrect:
      {{ incorrectCount }}
    </p>
    <div class="n-icon">
      <i :class="['fa', icon]" aria-hidden="true"></i>
    </div>
    <div class="n-buttons">
      <button>Old</button>
      <button>New</button>
    </div>
  </div>
</template>

<script>
import FONT_AWESOME_ICONS from '../js/font-awesome-icons.js';
export default {
  name: 'NewIcon',
  data() {
    return {
      correctCount: 0,
      incorrectCount: 0,
      iconIndex: 0,
      iconSource: FONT_AWESOME_ICONS.sort(() => Math.random() - 0.5)
        .slice(0, 120)
        .map((icon, idx) => ({ idx: idx, icon: icon, new: true })),
    };
  },
  computed: {
    score: function () {
      return this.correctCount - this.incorrectCount;
    },
    icon: function () {
      return this.iconSource[this.iconIndex].icon;
    },
  },
};
</script>

<style lang="scss" scoped>
.n-outer {
  display: flex;
  flex-direction: column;
  gap: 24px;
}
.n-icon {
  align-self: center;
}
i {
  font-size: 600px;
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
@media (max-width: 800px) {
  i {
    font-size: 320px;
  }
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
