---
title: vue组件通讯
date: 2016-11-27 18:03:24
tags:
---
### vue组件通讯
A：父组件，B：子组件

A组件：使用B组件时候加入v-model绑定需要输出的数据
 ```javascript
 <template lang="html">
   <div>
     <h3>{{title}}</h3>
     <div>输出B组件输入框的数据：{{message}}</div>//输出B组件的数据
     <Bcomp v-model="message"></Bcomp>//使用v-model
   </div>
 </template>

 <script>
 import Bcomp from './B.vue'
 export default {
   data() {
     return {
       title: 'A组件',
       message: ''
     }
   },
   components: {
     Bcomp
   }
 }
 </script>
 ```
B组件：
 ```javascript
 <template lang="html">
   <div>
     <input type="text"
     ref="Binput"//索引ID
     :value="value"//传递的数据
     @input="updateValue($event.target.value)"//输入时候触发input绑定的事件
     >
   </div>
 </template>

 <script>
 export default {
   props: ['value'],//需要传递的数据
   methods: {
     updateValue(value) {
       this.$emit('input', this.$refs.Binput.value)//触发input事件，传递索引ID的值
     }
   }
 }
 </script>

 <style lang="css">
 input[type="text"] {
   border: 1px solid black;
 }
 </style>
 ```
