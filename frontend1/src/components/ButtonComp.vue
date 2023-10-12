<template>
  <div
    :class="{
      'button-container-default' : buttonType === 0,
      'button-container-white' : buttonType === 1
    }"
    @click = "clickBtn"
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
      this.$emit('btnClicked', this.buttonContent);
    },
  }
}
</script>

<style lang="scss" scoped>
  @mixin common-state {
    width: 100%;
    height: 100%;
    padding: 2px;
    border-radius: 4px;
    white-space: nowrap;
    font-size: 1px;
  }
  .button-container-default {
    @include common-state;

    background-color: rgba(142, 142, 142, 1.0);
    border: 1px solid rgba(217, 217, 217, 1.0);

    color: rgba(255, 255, 255, 1.0);
  }

  .button-container-default:hover {
    @include common-state;

    background-color: rgba(222, 222, 222, 1.0);
    border: 1px solid rgba(37, 42, 169, 0.5);

    color: rgba(0, 0, 0, 1.0);

    cursor: pointer;
  }
</style>
