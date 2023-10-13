<template>
  <div class="test-container">
    <a class="test-container__title"># Button Types</a>
    <div class="test-container__button-part">
      <ButtonComp
          button-content="default button"
          @btnClicked="handleButtonClick"
      ></ButtonComp>
    </div>
    <div class="test-container__button-part">
      <ButtonComp
          button-content="button 1"
          :button-type="1"
          @btnClicked="handleButtonClick"
      ></ButtonComp>
    </div>
    <br>
    <br>
    <a class="test-container__title"># Input Fields</a>
    <div class="test-container__input-field-part">
      <input-field-comp
          @getInputMessage="handleInputMessage"
      />
    </div>
    <div class="test-container__input-field-part">
      <input-field-comp
        :has-submit-button="true"
        @getInputMessage="handleInputMessage"
      >
      </input-field-comp>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
import InputFieldComp from "@/components/InputFieldComp.vue";

export default {
  name: "TestView",
  components: {InputFieldComp, ButtonComp},
  methods: {
    handleButtonClick(buttonContent) {
      console.log("Button clicked! Content: " + buttonContent);
    },
    handleInputMessage(inputMessage) {
      console.log("Input Message: " + inputMessage);
    }
  },
}
</script>

<style lang="scss" scoped>
  @mixin part-common {
    display: flex;
    flex-direction: column;
    margin: 2px 0;
  }

  .test-container {
    margin: 8px;
    display: flex;
    flex-direction: column;

    &__title {
      display: flex;
      font-size: 20px;
      margin: 2px 0;
    }

    &__button-part {
      @include part-common;
    }

    &__input-field-part {
      @include part-common;

      width: 200px;
      height: 40px;
    }
  }
</style>
