<script setup>
import { ref } from 'vue'

// v-for 搭配陣列來使用
// v-bind:key=""  會影響渲染效率及渲染結果，必須加上
// v-bind:key="key" ，如果陣列資料沒有id的寫法
// v-bind:key="item.id"
const array = ref([
  {
    id: 1,
    name: '小明',
    age: 18
  },
  {
    id: 2,
    name: '小美',
    age: 16
  },
  {
    id: 3,
    name: '漂亮阿姨',
    age: 20
  }
])

// v-if , v-else, v-show
// v-if 與 v-for 不要寫在同一行，只能以包覆型式使用
const isChecked = ref(false)
</script>

<template>
  <div>
    姓名:{{ array[0].name }} 年齡:{{ array[0].age }}
    <hr />
  </div>

  <div v-for="(item, key) in array" v-bind:key="item.id">
    索引: {{ key }} 姓名:{{ item.name }} 年齡:{{ item.age }}
    <hr />
  </div>

  <div v-for="(item, key) in array" v-bind:key="item.id">
    索引: {{ key }} 姓名:{{ item.name }} 年齡:{{ item.age }}
    <div v-if="item.age > 18">大於18歲</div>
    <div v-else>小於18歲</div>
    <hr />
  </div>

  <hr />

  <input type="checkbox" v-model="isChecked" /> {{ isChecked }}

  <div>
    <h1 v-if="isChecked">當 isChecked == true 會顯示這行</h1>
    <h1 v-else>目前的 isChecked 為 false</h1>

    <h1 v-show="isChecked">當 isChecked 為 false ， 切換成display:none</h1>
  </div>

  <!-- v-for -->
  <!-- v-for="(item, key) in array" v-bind:key="key"-->
  <!-- v-for="(item, key) in array" v-bind:key="item.id"-->
  <!-- 陣列的索引為 0, 1, 2...，物件索引則為屬性名稱-->>
</template>

<style></style>
