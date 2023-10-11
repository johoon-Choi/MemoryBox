<template>
  <div class="test-container">
    <div class="test-container__part">
      <a class="test-container__part__title"> Button Types</a>
      <ButtonComp button-content="default button"></ButtonComp>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
export default {
  name: "TestView",
  components: {ButtonComp}
}
</script>

<style lang="scss" scoped>
  .test-container {
    margin: 8px;
    display: flex;
    flex-direction: column;

    &__part {
      display: flex;
      flex-direction: column;

      &__title {
        display: flex;
        font-size: 12px;
        margin: 0 0 4px 0;
      }
    }
  }
</style>
