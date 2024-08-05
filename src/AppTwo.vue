<script setup>
import { ref } from 'vue'

// v-on

const handleClick = () => {
  console.log('我被觸發了')
}

const submitForm = () => {
  console.log('表單被觸發了')
}

const text = ref('一段文字')
</script>

<template>
  <div>
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <form action="" @submit="submitForm">
      <button type="button" v-on:click="handleClick">點我</button>
      <br />
      <button type="button" @click="handleClick">點我</button>
      <br />
      <button type="submit">非button型式，畫面會refresh，預設type為 submit</button>
    </form>
  </div>
  <h2>事件修飾符 prevent</h2>
  <a href="#" @click="handleClick">點我，會刷新到頁面最上面</a>
  <br />
  <a href="#" @click.prevent="handleClick">prevent會清除掉html預設事件</a>
  <br />
  <h2>按鍵修飾符 enter後才觸發</h2>
  <input type="text" v-on:keydown.enter="handleClick" />
  <br />
  <h2>按鍵修飾符，加上綁定預設文字</h2>
  <input type="text" v-model="text" v-on:keydown.enter="handleClick" />

  <!-- v-on:click="counter += 1" -->
  <!-- v-on:click="say('hi')" -->

  <!-- 移除預設事件後會執行觸發器內的事件 -->
  <!-- v-on:click.prevent="" -->

  <!-- 修飾按鍵符 -->
  <!-- @keyup.enter="" -->
  <!-- @keyup.a="" -->
</template>

<style></style>
