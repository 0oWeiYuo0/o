<script setup>
import { ref } from "vue";
import axios from "axios";

const site = 'https://todolist-api.hexschool.io';

// Sign Up

const emailSignUp = ref('');
const passwordSignUp = ref('');
const nickNameSignUp = ref('');
const messageSignUp = ref('');


const SignUp = () => {
  if (emailSignUp.value === '' || passwordSignUp.value === '' || nickNameSignUp.value === '') {
    alert('請先輸入所有欄位');
  } else {
    try {
      console.log('點擊了註冊');
      const response = axios.post(`${site}/users/sign_up`, {
        "email": emailSignUp.value,
        "password": passwordSignUp.value,
        "nickname": nickNameSignUp.value
      })
      messageSignUp.value = `註冊成功`
    } catch (error) {
      messageSignUp.value = `註冊失敗：${error.response.data.message}`
    }
  }
}

// Sign In
const emailSignIn = ref('');
const passwordSignIn = ref('');
const messageSignIn = ref('');

const SignIn = async () => {
  if (emailSignIn.value === '' || passwordSignIn.value === '') {
    alert('請先輸入所有欄位')
  } else {
    try {
      console.log('點擊了登入');
      const response = await axios.post(`${site}/users/sign_in`, {
        "email": emailSignIn.value,
        "password": passwordSignIn.value
      })
      messageSignIn.value = `登入成功 ${response.data.token}`

    } catch (error) {
      messageSignIn.value = `登入失敗，原因：${error.response.data.message}`
    }
  }
}

</script>

<template>
  <div class="CRUD">
    <div>
      <h1>註冊</h1>
      <input type="email" placeholder="Email" v-model="emailSignUp">
      <input type="password" placeholder="Password" v-model="passwordSignUp">
      <input type="text" placeholder="nickName" v-model="nickNameSignUp">
      <button @click="SignUp">註冊</button>
      <p>{{ messageSignUp }}</p>
    </div>
    <div>
      <h1>登入</h1>
      <input type="email" placeholder="Email" v-model="emailSignIn">
      <input type="password" placeholder="Password" v-model="passwordSignIn">
      <button @click="SignIn">登入</button>
      <p>{{ messageSignIn }}</p>
    </div>

  </div>
</template>

<style lang="scss" scoped>
button {
  background-color: white;
  color: black;
}
</style>