<template>
  <div class="login-container">
    <div class="login-container__login-box">
      <h1 class="login-container__login-box__title">Login To Memory Box</h1>
      <input-field-comp
          class="login-container__login-box__input-field"
          @getInputMessage="handleIdInput"
          :placeholder-content="'input id'"
      >
      </input-field-comp>
      <input-field-comp
          class="login-container__login-box__input-field"
          @getInputMessage="handlePasswordInput"
          :placeholder-content="'input password'"
      >
      </input-field-comp>
      <button-comp
          class="login-container__login-box__login-button"
        button-content="Log-in"
          @btnClicked="doLogIn"
      ></button-comp>
      <a class="login-container__login-box__or">OR</a>

      <div
        class="login-container__login-box__social-button"
        @click="doSocialLogin('Google')"
      >
        <div class="login-container__login-box__social-button__google-logo">
        </div>
        <div>
          Continue with Google
        </div>
      </div>

      <div
          class="login-container__login-box__social-button"
          @click="doSocialLogin('Naver')"
      >
        <div class="login-container__login-box__social-button__naver-logo">
        </div>
        <div>
          Continue with Naver
        </div>
      </div>

      <row-line class="login-container__login-box__row-line"></row-line>

      <div class="login-container__login-box__foot">
        <div class="login-container__login-box__foot__side"
          @click="doSignUp"
        >
          Do you want to Sign up?
        </div>
        <col-line></col-line>
        <div
          class="login-container__login-box__foot__side"
          @click="findPassword"
        >
          Lost your password?
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ButtonComp from "@/components/ButtonComp.vue";
import InputFieldComp from "@/components/InputFieldComp.vue";
import RowLine from "@/components/RowLine.vue";
import ColLine from "@/components/ColLine.vue";

export default {
  name: "LoginView",
  components: {ColLine, RowLine, ButtonComp, InputFieldComp},
  data() {
    return {
      id: "",
      pw: ""
    }
  },
  methods: {
    handleIdInput(id) {
      this.id = id;
    },
    handlePasswordInput(pw) {
      this.pw = pw;
    },
    doLogIn() {
      console.log(" id: " + this.id);
      console.log(" pw: " + this.pw);
    },
    doSocialLogin(target) {
      console.log(" TARGET: " + target);
    },
    doSignUp() {
      console.log(" need to sign up");
    },
    findPassword() {
      console.log(" need to find pw");
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

      &__row-line {
        margin: 8px 0;
      }

      &__foot {
        display: flex;
        justify-content: space-around;
        width: 100%;

        &__side {
          display: flex;
          cursor: pointer;
        }
      }
    }
  }
</style>
