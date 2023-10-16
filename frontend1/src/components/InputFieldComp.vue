<template>
  <div
    :class="{
    'input-field-default-container' : fieldType === 0,
    }"
  >
    <input
      v-model="input"
      type="text"
      class="input-field-default-container__input-box"
      :placeholder="placeholderContent"
      @keyup="handleKeyDown($event)"
    >
    <div
      v-if="hasSubmitButton"
      class="input-field-container__button"
    >
      <ButtonComponent
          button-content="입력"
          :button-type="1"
          @btnClicked="handleButtonClick"
      />
    </div>
  </div>
</template>

<script>
import ButtonComponent from "@/components/ButtonComp.vue";

export default {
  name: "InputFieldComp",
  components: {
    ButtonComponent
  },
  props: {
    fieldType: {
      type: Number,
      required: false,
      default: 0
    },
    hasSubmitButton: {
      type: Boolean,
      required: false,
      default: false
    },
    isDeleteAfterSubmit: {
      type: Boolean,
      required: false,
      default: false
    },
    placeholderContent: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      input: "",
    }
  },
  methods: {
    handleKeyDown(event) {
      console.log("Key downed! event: " + event.key);
      if (!this.hasSubmitButton) {
        this.handleButtonClick();
      }
    },
    handleButtonClick() {
      console.log("Button clicked! inputMessage: " + this.input);
      this.$emit('getInputMessage', this.input);
      if (this.isDeleteAfterSubmit) {
        this.input = "";
      }
    },
  },
}
</script>

<style lang="scss" scoped>
  @import "@/assets/css/HoverCommon.scss";

  .input-field-default-container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;

    width: 100%;
    height: 100%;

    border: 1px solid rgba(217, 217, 217, 1.0);
    background-color: rgba(255, 255, 255, 1.0);

    padding: 0 4px;

    input:focus {outline:none;}

    &__input-box {
      width: 98%;
      border: 1px solid transparent;
      background-color: transparent;
    }

    &__input-box {
      width: 98%;
      border: 1px solid transparent;
      background-color: transparent;
    }

    &__button {
      display: flex;
      flex-direction: column;
    }
  }

  .input-field-default-container:hover {
    @include input-field-hover-common;
  }

  .input-field-default-container:focus-within {
    @include input-field-hover-common;
  }
</style>
