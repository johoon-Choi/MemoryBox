<template>
  <div :class="{
    'drop-box-container': !isClicked,
    'drop-box-container-clicked': isClicked
  }"
    @click="handleClickEvent"
  >
    <div class="drop-box-container__title">
      title
    </div>
    <div :class="{
    'drop-box-container__downward-triangle': !isClicked,
    'drop-box-container__upward-triangle': isClicked
  }">
    </div>
    <div
      v-if="isClicked"
      class="drop-box-container__list-box"
    ></div>
  </div>
</template>

<script>
export default {
  name: "DropBox",
  data() {
    return {
      isClicked: false,
      data: ['Seoul', 'Incheon', 'Busan']
    }
  },
  methods: {
    handleClickEvent() {
      this.isClicked = !this.isClicked;
    }
  }
}
</script>

<style lang="scss" scoped>
  .drop-box-container {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;

    width: 100%;
    height: 100%;

    background-color: #D9D9D9;
    color: #3D3D3D;

    -webkit-user-select: none;
    -moz-user-select: none;
    user-select: none;

    border: 1px solid transparent;
    border-radius: 4px;

    &:hover {
      border: 1px solid #8E8E8E;
    }

    &__title {
      display: flex;
      width: 70%;
    }

    &__downward-triangle {
      display: flex;
      width: 12px;
      height: 12px;
      background-image: url("@/assets/icons/triangle_down.png");
      background-size: 100% auto;
      background-repeat: no-repeat;
      background-position: 50% 50%;
    }
    &__upward-triangle {
      display: flex;
      width: 12px;
      height: 12px;
      background-image: url("@/assets/icons/triangle_up_hover.png");
      background-size: 100% auto;
      background-repeat: no-repeat;
      background-position: 50% 50%;
    }

    &__list-box {
      position: fixed;
      background-color: #42b983;
      left: 0;
      top: 0;
      width: 100%;
      height: 200px;
    }
  }

  .drop-box-container:hover .drop-box-container__downward-triangle {
    background-image: url("@/assets/icons/triangle_down_hover.png");
  }

  .drop-box-container-clicked {
     display: flex;
     justify-content: center;
     align-items: center;

     width: 100%;
     height: 100%;

     background-color: #D9D9D9;
     color: #3D3D3D;

     -webkit-user-select: none;
     -moz-user-select: none;
     user-select: none;

     border: 1px solid transparent;
     border-top-left-radius: 4px;
    border-top-right-radius: 4px;

     &:hover {
       border: 1px solid #8E8E8E;
     }

     &__title {
       display: flex;
       width: 70%;
     }

     &__downward-triangle {
       display: flex;
       width: 12px;
       height: 12px;
       background-image: url("@/assets/icons/triangle_up_hover.png");
       background-size: 100% auto;
       background-repeat: no-repeat;
       background-position: 50% 50%;
     }
   }
</style>
