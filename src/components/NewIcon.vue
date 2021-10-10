<template>
  <div class="n-outer">
    <h1>New Icon</h1>
    <h2>Please identify the new icons.</h2>
    <p>
      Current score: {{ score }}, correct: {{ correctCount }}, incorrect:
      {{ incorrectCount }}
    </p>
    <div class="n-icon">
      <i class="fa fa-smile-o" aria-hidden="true"></i>
    </div>
    <div class="n-buttons">
      <button>Old</button>
      <button>New</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewIcon',
  data() {
    return { correctCount: 0, incorrectCount: 0 };
  },
  computed: {
    score: function () {
      return this.correctCount - this.incorrectCount;
    },
  },
};
</script>

<style lang="scss" scoped>
.n-outer {
  display: flex;
  flex-direction: column;
}
.n-icon {
  align-self: center;
}
i {
  font-size: 600px;
}
.n-buttons {
  display: flex;
  justify-content: space-around;
}
button {
  padding: 24px;
  font-size: 36px;
}
</style>
