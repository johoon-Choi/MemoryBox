<template>
  <div class="button-container">
    <div
      @click="clickBtn"
      :class="{
      'button-container__default' : buttonType === 0,
      'button-container__white' : buttonType === 1
    }">
      {{ buttonContent }}
    </div>
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
      console.log(" button type : " + this.buttonType);
      this.$emit('btnClicked', this.buttonContent);
    },
  }
}
</script>

<style lang="scss" scoped>
  @import "@/assets/css/HoverCommon.scss";

  @mixin common-state {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    padding: 2px;
    border-radius: 4px;
    white-space: nowrap;
    font-size: 100%;
  }

  .button-container {
    display: flex;

    &__default {
      @include common-state;

      background-color: rgba(142, 142, 142, 1.0);
      border: 1px solid rgba(217, 217, 217, 1.0);

      color: rgba(255, 255, 255, 1.0);
    }

    &__default:hover {
      @include common-state;
      @include hover-common;

      background-color: rgba(222, 222, 222, 1.0);

      color: rgba(0, 0, 0, 1.0);

      cursor: pointer;
    }

    &__white {
      @include common-state;

      background-color: rgba(217, 217, 217, 1.0);
      border: transparent;

      color: rgba(0, 0, 0, 1.0);
    }

    &__white:hover {
      @include common-state;
      @include hover-common;

      background-color: rgba(111, 111, 111, 1.0);
      border: transparent;

      color: rgba(0, 0, 0, 1.0);

      cursor: pointer;
    }
  }
</style>
