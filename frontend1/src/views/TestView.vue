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
          :placeholder-content="'a'"
      />
    </div>
    <div class="test-container__input-field-part">
      <input-field-comp
        :has-submit-button="true"
        :placeholder-content="'b'"
        @getInputMessage="handleInputMessage"
      >
      </input-field-comp>
    </div>
    <a class="test-container__content"> Input Message: {{inputMessage}}</a>

    <br>
    <br>
    <a class="test-container__title"># block Types</a>
    <block-comp
        class="test-container__block"
      :block-type="1"
    >
      <div class="test-container__block__block-inside"></div>
    </block-comp>

    <br>
    <br>
    <a class="test-container__title"># Row Line</a>
    <row-line></row-line>

    <br>
    <br>
    <a class="test-container__title"># Col Line</a>
    <div class="test-container__col-test">
      <div class="test-container__col-test__temp-block">
        aaa
      </div>
      <col-line></col-line>
      <div class="test-container__col-test__temp-block">
        bbb
      </div>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
import InputFieldComp from "@/components/InputFieldComp.vue";
import BlockComp from "@/components/BlockComp.vue";
import RowLine from "@/components/RowLine.vue";
import ColLine from "@/components/ColLine.vue";

export default {
  name: "TestView",
  components: {ColLine, RowLine, BlockComp, InputFieldComp, ButtonComp},
  data() {
    return {
      inputMessage: "",
    }
  },
  methods: {
    handleButtonClick(buttonContent) {
      console.log("Button clicked! Content: " + buttonContent);
    },
    handleInputMessage(inputMessage) {
      this.inputMessage = inputMessage;
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
    align-items: flex-start;

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

    &__content {
    }

    &__block {
      width: 200px;
      height: 40px;
    }

    &__col-test {
      display: flex;

      &__temp-block {
        display: flex;
      }
    }
  }
</style>
