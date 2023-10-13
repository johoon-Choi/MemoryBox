<template>
  <div class="block-container">
    <div
      :class="{
      'block-container__default' : blockType === 0,
      'block-container__under-shadow' : blockType === 1
    }">
    </div>
  </div>
</template>

<script>
export default {
  name: "BlockComp",
  props: {
    blockType: {
      type: Number,
      required: false,
      default: 0
    },
  }
}
</script>

<style lang="scss" scoped>
  .block-container {
    display: flex;
    width: 100%;
    height: 100%;

    &__default {

    }

    &__under-shadow {
      width: 100%;
      height: 100%;

      background-color: rgba(255, 255, 255, 1.0);
      border: 1px solid rgba(244, 244, 244, 1.0);
      box-shadow: 1px 1px 4px 1px rgba(222, 222, 222, 1.0);
    }
  }
</style>
