<template>
  <label class="text-edit">
    <textarea
        v-model="textValue"
        class="text-edit__input"
        @focus="editing = true"
        @blur="editing = false"
    />
    <div
        class="text-edit__text"
        :class="{'text-edit__text--active': editing}"
    >
      <span
          class="text-edit__text-line"
          v-for="(textLine, index) in textToShow"
          :key="index"
          v-text="textLine"
      />
    </div>
  </label>
</template>

<script>
export default {
  name: 'TextEdit',
  data() {
    return {
      textValue: 'Ola',
      editing: false,
    }
  },
  computed: {
    textToShow() {
      return this.textValue.split('\n');
    },
  }
}
</script>

<style lang="less">
.text-edit {
  position: relative;
  display: flex;

  border: 3px solid transparent;

  &:hover {
    border: 3px solid #42b983;
    cursor: pointer;
  }
}

.text-edit__input {
  position: absolute;
  width: 0;
  right: 0;

  color: transparent;
  border: 0 transparent;

  overflow: hidden;
  opacity: 0;

  &:focus {
    outline: none;
  }
}

.text-edit__text {
  display: flex;
  flex-direction: column;
}

.text-edit__text-line {
  width: fit-content;
  display: flex;
  flex-wrap: wrap;
}

.text-edit__text--active {

  .text-edit__text-line {

    &:last-of-type {

      .blinking-cursor();
    }
  }
}

.blinking-cursor() {
  border-right: 1px black solid;

  animation: blink 1s;
  animation-iteration-count: 3;
}

@keyframes blink { 50% { border-color:#fff ; }  }
</style>