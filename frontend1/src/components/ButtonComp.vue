<template>
  <div
    :class="{
      'button-container__default' : buttonType === 0,
      'button-container__white' : buttonType === 1
    }"
  >
    {{ buttonContent }}
  </div>
</template>

<script>
export default {
  name: "ButtonComp",
  props: {
    buttonType: {
      type: Number,
      required: false,
      default: 0
    },
    buttonContent: {
      type: String,
      required: true,
    },
  },
  methods: {
    clickBtn() {
      this.$emit('btnClicked');
    },
  }
}
</script>

<style lang="scss" scoped>
  .button-container {
    display: inline-block;
    padding: 4px;

    &__default {
      background-color: rgba(142, 142, 142, 1.0);
      border: 1px solid rgba(217, 217, 217, 1.0);

      font-size: 8px;
      color: rgba(255, 255, 255, 1.0);

      border-radius: 4px;
    }

    &__default:hover {
      background-color: rgba(166, 166, 166, 1.0);
      border: 1px solid rgba(100, 100, 100, 1.0);

      font-size: 8px;
      color: rgba(0, 0, 0, 1.0);

      border-radius: 4px;
    }
  }
</style>
