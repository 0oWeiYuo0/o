<script setup>

import { ref, computed } from "vue";

const password = ref('');

const isLongEnough = computed(() => {
  return password.value.length >= 12
})
const hasLetter = computed(() => {
  return /[A-Za-z]/.test(password.value)
})
const hasNumber = computed(() => {
  return /[0-9]/.test(password.value)
})
const hasSpecialChar = computed(() => {
  return /[!@#$%^&*(),.?":{}|<>]/.test(password.value)
})

</script>

<template>
  <div class="passwordHint">
    <h1>設定密碼</h1>
    <input class="password" type="password" placeholder="請輸入密碼" v-model="password">
    <div class="hints">
      <div :class="{ 'met': isLongEnough }">至少 12 個字符</div>
      <div :class="{ 'met': hasLetter }">包含字母</div>
      <div :class="{ 'met': hasNumber }">包含數字</div>
      <div :class="{ 'met': hasSpecialChar }">包含特殊符號</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
body {
  width: 100%;
  margin: auto;

  #app {
    display: flex;
    justify-content: center;
  }

  .passwordHint {
    width: 800px;
    height: 280px;
    border: 1px solid white;
    border-radius: 10px;

    >h1 {
      text-align: center;
      margin-top: 1rem
    }

    >input {
      width: 50%;
      display: block;
      margin: auto;
      padding: 1rem;
      background-color: #141414;
      color: white;
      border: none;
      outline: none;

    }

    >.hints {
      margin-top: 10px;
      width: 100%;
      display: flex;
      justify-content: center;
      gap: 15px;

      >div {
        color: gray;
        font-weight: bold;
        border: 1px solid gray;
        border-radius: 25px;
        padding: .5rem 1rem;

        &.met {
          color: white;
          background-color: green;
        }
      }
    }
  }
}
</style>