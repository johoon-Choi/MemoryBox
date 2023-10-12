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
          @btnClicked="handleButtonClick"
      ></ButtonComp>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
export default {
  name: "TestView",
  components: {ButtonComp},
  methods: {
    handleButtonClick(buttonContent) {
      console.log("Button clicked! Content: " + buttonContent);
    },
  },
}
</script>

<style lang="scss" scoped>
  .test-container {
    margin: 8px;
    display: flex;
    flex-direction: column;

    &__title {
      display: flex;
      font-size: 12px;
      margin: 2px 0;
    }

    &__button-part {
      display: flex;
      flex-direction: column;
      width: min-content;
      margin: 2px 0;
    }
  }
</style>
