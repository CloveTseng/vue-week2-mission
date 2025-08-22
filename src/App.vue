<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'

const baseUrl = 'https://todolist-api.hexschool.io'
const signUpRes = ref('')
const signInRes = ref('')
const signupField = ref({
  email: '',
  password: '',
  nickname: '',
})
const signinField = ref({
  email: '',
  password: '',
})
const userSignIn = ref({
  nickname: '',
  uid: '',
})

const signUp = async () => {
  try {
    const res = await axios.post(`${baseUrl}/users/sign_up`, signupField.value)
    signUpRes.value = res.data.uid
    alert('註冊成功')
  } catch (error) {
    console.log(error)
  }
}
const signIn = async () => {
  try {
    const res = await axios.post(`${baseUrl}/users/sign_in`, signinField.value)
    signInRes.value = res.data
    document.cookie = `customToken=${res.data.token};`
    alert('登入成功')
  } catch (error) {
    console.log(error)
  }
}
// 驗證登入
onMounted(async () => {
  const token = document.cookie.replace(/(?:(?:^|.*;\s*)customToken\s*=\s*([^;]*).*$)|^.*$/, '$1')
  console.log(token)
  const res = await axios.get(`${baseUrl}/users/checkout`, {
    headers: {
      authorization: token,
    },
  })
  userSignIn.value = res.data
  console.log(res)
})
</script>
<template>
  <div class="m-5">
    <h1 class="text-3xl text-orange-700 font-bold">Vue - 第二週作業</h1>
    <h2>親愛的用戶：{{ userSignIn.nickname }}</h2>
    <h3>歡迎回來</h3>
    <form action="" class="mt-5">
      <div>
        <label for="emailSignUp" class="block">帳號</label>
        <input
          type="email"
          id="emailSignUp"
          placeholder="請輸入帳號(Email)"
          class="input-form border rounded-sm p-2"
          v-model="signupField.email"
          autocomplete="current-emailSignUp"
        />
      </div>
      <div class="mt-2">
        <label for="passwordSignUp" class="block">Password</label>
        <input
          type="password"
          id="passwordSignUp"
          placeholder="請輸入密碼"
          class="input-form border rounded-sm p-2"
          v-model="signupField.password"
          autocomplete="current-password"
        />
      </div>
      <div class="mt-2">
        <label for="nicknameSignUp" class="block">nickname</label>
        <input
          type="text"
          id="nicknameSignUp"
          placeholder="請輸入暱稱"
          class="input-form border rounded-sm p-2"
          v-model="signupField.nickname"
        />
      </div>
      <div>
        <button
          type="button"
          @click="signUp"
          class="border rounded-sm px-3 py-1 border-amber-300 m-1 cursor-pointer"
        >
          註冊
        </button>
      </div>
    </form>
    <form action="" class="mt-5">
      <div>
        <label for="emailSignIn" class="block">帳號</label>
        <input
          type="email"
          id="emailSignIn"
          placeholder="請輸入帳號(Email)"
          class="input-form border rounded-sm p-2"
          v-model="signinField.email"
        />
      </div>
      <div class="mt-2">
        <label for="passwordSignIn" class="block">Password</label>
        <input
          type="password"
          id="passwordSignIn"
          placeholder="請輸入密碼"
          class="input-form border rounded-sm p-2"
          v-model="signinField.password"
          autocomplete="current-password"
        />
      </div>
      <div>
        <button
          type="button"
          @click="signIn"
          class="border rounded-sm px-3 py-1 bg-amber-300 m-1 border-amber-300 cursor-pointer"
        >
          登入
        </button>
      </div>
    </form>
  </div>
</template>
