<script setup>
// script setup 寫法和cdn方式不同，不用return

import { ref } from 'vue'

const num = ref(2)
//   console.log(num);
console.log(num.value)

function clickMe() {
  num.value++
}

const text = ref('這是一段文字')
const city = ref('台北市')
const isChecked = ref(true)
const arrayCheckbox = ref([])
const radioValue = ref('男')

const num2 = ref(0)
const htmlTemplate = `<h1>這是 HTML 片段<h1>`

setInterval(() => {
  num2.value++
}, 500)

const imgUrl = ref(
  'https://images.unsplash.com/photo-1487530811176-3780de880c2d?w=400&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8Zmxvd2VyJTIwYm91cXVldHxlbnwwfHwwfHx8MA%3D%3D'
)

const isChecked2 = ref(false)

// return { num, clickMe };
</script>

<template>
  <div>
    <!-- 點擊函式，這邊的 num 不需要寫成 num.value-->
    {{ num }}
    <button type="button" v-on:click="clickMe">點我</button>

    <h1>{{ text }}</h1>
    <!-- v-model 雙向綁定-->
    <input type="text" v-model="text" />

    <!-- 表單 -->

    {{ city }}
    <select name="" id="" v-model="city">
      <!-- 顯示的值為option的內容，實際儲存的值看value -->
      <option value="台北市">台北市</option>
      <option value="台中市">2222</option>
      <option value="高雄市">333</option>
    </select>
    <hr />

    <!-- checkbox 1.true false 2.value -->
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <hr />

    <!-- 存放陣列的值 -->
    {{ arrayCheckbox }}
    <input type="checkbox" v-model="arrayCheckbox" value="漂亮阿姨" />
    <input type="checkbox" v-model="arrayCheckbox" value="小明" />
    <input type="checkbox" v-model="arrayCheckbox" value="杰倫" />
    <hr />

    <!-- radio 存放單一值 -->
    {{ radioValue }}
    <input type="radio" v-model="radioValue" value="男" />
    <input type="radio" v-model="radioValue" value="女" />
    <hr />

    <!-- 兩種顯示方式 -->
    {{ num2 }}
    <h1>這個數值目前是: {{ num2 }}</h1>
    <!-- v-text 指令 -->
    <h1 v-text="num2"></h1>
    <hr />

    {{ htmlTemplate }}
    <div v-text="htmlTemplate"></div>
    <!-- v-html 才會套用html標籤 -->
    <div v-html="htmlTemplate"></div>
    <hr />

    <!-- v-bind: -->
    <!-- : 為縮寫形式 -->
    <img v-bind:src="imgUrl" alt="" />
    <br />
    <img :src="imgUrl" alt="" />
    <br />

    <!-- v-bind ，可以套用在任何屬性上，後面接的是物件的形式 -->
    {{ isChecked2 }}
    <input type="checkbox" v-model="isChecked2" />
    <input type="text" v-bind:disabled="isChecked2" />
    <h2>可以套用在行內樣式上</h2>
    <div class="box" style="transform: rotate(45deg)"></div>
    <br />
    <!-- v-bind 通常對變數的部分進行替換 'rotate(45deg)' -->
    <div class="box" v-bind:style="{ transform: 'rotate(45deg)' }"></div>
    <br />
    <!-- 三元運算子 -->
    <div class="box" v-bind:style="{ transform: isChecked2 ? 'rotate(45deg)' : null }"></div>
    <br />
    <!-- background-color 換成小駝峰寫法-->
    <div class="box" :style="{ backgroundColor: isChecked2 ? 'red' : 'green' }"></div>

    <h2>class</h2>
    <!-- 需要套用的 className， 變數-->
    <div class="box" v-bind:class="{ rotate: isChecked2 ? 'rotate' : null }"></div>
  </div>

  <!-- v-model.lazy -->
  <!-- 當 input 編輯時，無法直接修改畫面上的值，需要離開 input 時才會觸發 -->

  <!-- v-model.number -->
  <!-- .number 的修飾符，確保用戶所輸入的為純數值 -->

  <!-- v-model.trim -->
  <!-- trim：修飾掉首尾的空白 -->

  <!-- select 表單，option -->
  <!-- select 所綁定的 v-model 其值來自於 <option></option> 內的 value -->

  <!-- v-bind -->
  <!-- 動態地綁定 HTML 屬性，將資料傳遞到元素上 -->
  <!-- 動態地綁定 HTML 屬性，將資料傳遞到元素上 -->
  <!-- 可以使用各種 JS 的表達式 -->
  <!-- v-bind:value="text" -->
  <!-- :value="1 + 1" -->
  <!-- :src="imgUrl" -->

  <!-- 物件中的前者為 className 名稱，後者為判斷式 -->
  <!-- 當為真值時則啟用前者的 className -->
  <!-- :class="{rotate: isTransform}" -->
  <!-- 傳入的是陣列，則可以直接啟用該 className -->
  <!-- :class="[...arrayClass]" -->

  <!-- 前者為 CSS 的屬性，後者為該屬性的值 -->
  <!-- :style="{backgroundColor: styleObject.backgroundColor}" -->
  <!-- 傳入的是陣列，則可以直接啟用該 className -->
  <!-- :style="[styleObject, styleObject2]" -->

  <!--  此值代表的是字串 1  -->
  <!--  input type="text" value="1"  -->

  <!--  此值代表的是數字 1  -->
  <!--  input type="text" v-bind:value="1"  -->
</template>

<style>
.box {
  height: 100px;
  width: 100px;
  background-color: red;
  transition: 0.5s all;
}

.rotate {
  transform: rotate(45deg);
}
</style>
