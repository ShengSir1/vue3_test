<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>我是APP组件</h1>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h2>性别：{{sex}}</h2>
  <h2>a:{{a}} --如果配置重名:vue3(setup)优先</h2>
  <button @click="sayHello">vue3方法</button>
  <button @click="sayWelcome">vue2方法</button>
  <button @click="test">vue2可以访问vue3的数据及方法</button>
  <button @click="test2">vue3不能访问vue2的数据及方法</button>
</template>

<script>
  import {h} from 'vue'
  export default {
  name: 'App',
  // vue2的写法
  data() {
    return {
      sex:'男',
      a:100
    }
  },
  methods: {
    sayWelcome(){
      alert('我是Vue2方法的写法')
    },
    test(){
      console.log(this.sex)
      console.log(this.name);
      console.log(this.age);
      console.log(this.sayHello);
    }
  },
  // vue3的写法
  setup() {
    // 数据
    let name ='大帅逼'
    let age = 19
    let a = 200
    // 方法
    function sayHello(){
      alert(`我是${name},我${age}岁了，你好潇鳖散`)
    }

    function test2(){
      console.log(name)
      console.log(age);
      console.log(sayHello);
      console.log(this.sex);
      console.log(this.sayWelcome);
    }
    
    // 返回一个对象(常用)
    return {
      name,
      age,
      sayHello,
      test2,
      a
    }

    // 返回一个函数（渲染函数）
    // return ()=> h('h1','唐职')

  }
}
</script>

<style>

</style>
