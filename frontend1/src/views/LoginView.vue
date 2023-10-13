<template>
  <div class="login-container">
    <div class="login-container__login-box">
      <h1 class="login-container__login-box__title">Login To Memory Box</h1>
      <input-field-comp
          class="login-container__login-box__input-field"
          :placeholder-content="'input id'"
      >
      </input-field-comp>
      <input-field-comp
          class="login-container__login-box__input-field"
          :placeholder-content="'input password'"
      >
      </input-field-comp>
      <button-comp
          class="login-container__login-box__login-button"
        button-content="Log-in"
      ></button-comp>
      <a class="login-container__login-box__or">OR</a>

      <div
        class="login-container__login-box__social-button"
        @click="login('Google')"
      >
        <div class="login-container__login-box__social-button__google-logo">
        </div>
        <div>
          Continue with Google
        </div>
      </div>

      <div
          class="login-container__login-box__social-button"
          @click="login('Naver')"
      >
        <div class="login-container__login-box__social-button__naver-logo">
        </div>
        <div>
          Continue with Naver
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
import InputFieldComp from "@/components/InputFieldComp.vue";

export default {
  name: "LoginView",
  components: {ButtonComp, InputFieldComp},
  methods: {
    login(target) {
      console.log(" button target: " + target);
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "@/assets/css/Block.scss";
  @mixin logo-common {
    display: flex;

    width: 20px;
    height: 20px;

    margin: 0 8px 0 0;
    background-size: cover;
  }

  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;

    width: 100vw;
    height: 100vh;

    &__login-box {
      display: flex;
      flex-direction: column;
      align-items: center;

      width: 400px;
      height: 400px;

      border: 1px solid rgba(0, 0, 0, 0.1);

      &__title {
        color: rgba(37, 42, 169, 1.0);
        font-size: 20px;
        font-weight: bolder;

        margin: 0 0 12px 0;
      }

      &__input-field {
        width: 96%;
        height: 28px;

        margin: 0 0 8px 0;
      }

      &__login-button {
        width: 98%;
        height: 28px;
        margin: 32px 0;
      }

      &__or {
        color: rgba(0, 0, 0, 1.0);
        margin: 0 0 32px 0;
        font-size: 20px;
        font-weight: bolder;
      }

      &__social-button {
        @include default-block;

        display: flex;
        align-items: center;
        justify-content: center;

        width: 96%;
        height: 28px;

        margin: 0 0 8px 0;

        cursor: pointer;

        &__google-logo {
          @include logo-common;
          background-image: url("@/assets/icons/GoogleLogo.png");
        }

        &__naver-logo {
          @include logo-common;
          background-image: url("@/assets/icons/NaverLogo.png");
        }
      }
    }
  }
</style>
