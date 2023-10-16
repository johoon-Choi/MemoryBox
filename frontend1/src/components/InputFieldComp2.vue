<template>
  <div class="input-field-container">
    <div class="input-field-container__text-input-field">
      <input
          v-model="input"
          class="input-field-container__text-input-field__input-area"
          :placeholder="placeholderContent"
          @keyup="handleKeyDown($event)"
      >
      <div class="input-field-container__text-input-field__delete-button"></div>
    </div>
    <div class="input-field-container__message-field">
      {{ Message }}
    </div>
  </div>
</template>

<script>

export default {
  name: "InputFieldComp",
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
    },
  },
  data() {
    return {
      input: "",
      Message: "Invalid message!"
    }
  },
  methods: {
    handleKeyDown(event) {
      console.log("Key downed! event: " + event.key);

      if (this.input.length < 5) { // Confirmed, Invalid 조건부
        this.Message = "Confirmed!";
      }

      else this.Message = "Invalid message!";
      this.handleSubmit();
    },
    handleSubmit() {
      this.$emit('getInputMessage', this.input);
      if (this.isDeleteAfterSubmit) {
        this.input = "";
      }
    },
  },
}
</script>

<style lang="scss" scoped>
  @import "src/assets/css/PathVariables";

  .input-field-container {
    display: flex;
    flex-direction: column;

    width: 100%;
    height: 100%;

    input:focus {outline:none;}

    &__text-input-field {
      display: flex;
      align-items: center;
      justify-content: center;

      border: $light-gray-color-border;
      border-radius: 4px;

      width: 100%;
      height: 100%;

      &:focus-within {
        border: $blue-color-border;
      }



      &__input-area {
        border: transparent;
        background-color: transparent;

        padding: 0;
        font-size: 20px;

        width: 84%;
        height: 100%;
      }

      &__delete-button {
        width: 20px;
        height: 20px;
        background-image: url("@/assets/icons/DeleteButton.png");
        background-size: cover; // image를 안 잘리고 안에 꽉 들어가게!
      }
    }

    &__message-field {
      display: flex;
      background-color: #42b983;

      margin: 2px 0 0 0;
      font-size: 4px;

      width: 100%;
      height: min-content;
    }
  }
</style>
