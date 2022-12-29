<template>
  <div class="container">

    <div class="wrapper">
      <button-component :type="button" link="https://vuejs.org/">Напомнить PIN-код</button-component>
    </div>

    <div class="wrapper">
      <button-component color="primary" :icon="arrowLeft"></button-component>
      <button-component color="danger" :icon="close"> </button-component>
      <button-component color="warning" :icon="quest"> </button-component>
      <button-component color="primary" :icon="arrowRight"> </button-component>
      <button-component color="danger" :icon="googlePlus"> </button-component>
      <button-component color="info" :icon="vk"> </button-component>
      <button-component color="action" :icon="classmates"> </button-component>
      <button-component color="primary" :icon="pencil"> </button-component>
    </div>

    <div class="wrapper">
      <button-component :time="3">Repeat letter</button-component>
    </div>

    <div class="wrapper">
      <button-component color="danger" type="button">send email</button-component>
      <button-component color="primary" type="submit">send email </button-component>
      <button-component color="secondary">send email</button-component>
      <button-component color="action">send email</button-component>
      <button-component color="warning">send email</button-component>
      <button-component color="info">send email</button-component>
      <button-component disabled="true">send email</button-component>
    </div>
  </div>
</template>

<script lang="ts">
import ButtonComponent from "./components/Button/button.vue";
import close from "./assets/icons/close.svg";
import vk from "./assets/icons/vk.svg";
import classmates from "./assets/icons/classmates.svg";
import arrowLeft from "./assets/icons/arrow-left.svg";
import arrowRight from "./assets/icons/arrow-right.svg";
import pencil from "./assets/icons/pencil.svg";
import quest from "./assets/icons/quest.svg";
import googlePlus from "./assets/icons/google-plus.svg";

export default {
  components: {
    ButtonComponent,
  },
  data() {
    return {
      close,
      googlePlus,
      quest,
      pencil,
      arrowLeft,
      arrowRight,
      classmates,
      vk,
    };
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
}
.wrapper {
  display: flex;
  flex-direction: column;
}

@media screen and (max-width: 768px) {
  .container {
    flex-direction: column;
    align-items: center;
  }
  .wrapper {
    margin-bottom: 20px;
  }
}
</style>
