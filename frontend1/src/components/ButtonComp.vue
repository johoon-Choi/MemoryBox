<template>
  <div class="button-container">
    <div
      @click="clickBtn"
      v-if="!needConfirm || !isClicked"
      :class="{
      'button-container__default' : buttonType === 0,
      'button-container__blue' : buttonType === 1
    }">
      {{ buttonContent }}
    </div>
    <div
      v-else-if="isClicked && needConfirm"
      class="button-container__confirmed"
    >
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
    needConfirm: {
      type: Boolean,
      required: false,
      default: false
    }
  },
  data() {
    return {
      isClicked: false,
    }
  },
  methods: {
    clickBtn() {
      this.isClicked = true;
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

    padding: 4px 12px;
    border-radius: 32px;

    white-space: nowrap;

    font-size: 12px;
  }

  .button-container {
    display: flex;

    &__default {
      @include common-state;
      background-color: #828282;
      color: #FFFFFF;
    }

    &__default:hover {
      @include common-state;
      background-color: #D9D9D9;
      cursor: pointer;
    }

    &__blue {
      @include common-state;
      background-color: #5C63FF;
      color: #FFFFFF;
    }

    &__blue:hover {
      @include common-state;
      background-color: #ABAEFF;
      cursor: pointer;
    }

    &__confirmed {
      @include common-state;
      background-color: #00C52B;
      color: transparent;
      background-image: url("@/assets/icons/Confirmed2.png");
      background-size: auto 16px;
      background-repeat: no-repeat;
      background-position: 50% 50%;
      -webkit-user-select: none;
      -moz-user-select: none;
      user-select: none;

    }
  }
</style>
