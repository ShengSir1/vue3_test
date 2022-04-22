<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息</h1>
  <h2 v-show="person.name">姓名：{{person.name}}</h2>
  <h2>年龄：{{person.age}}</h2>
  <h2 v-show="person.sex">性别：{{person.sex}}</h2>
  <h2>爱好：{{person.hobby}}</h2>
  <h3>岗位：{{person.job.type}}</h3>
  <h3>薪资：{{person.job.salary}}</h3>
  <button @click="changeInfo">修改这个人的信息</button>
  <button @click="addSex">添加一个sex属性</button>
  <button @click="deleteName">删除一个name属性</button>
</template>

<script>
  import {reactive} from 'vue' // reactive函数
  export default {
  name: 'App',
  setup() {
    // 数据
    let person = reactive({
      name:'张三',
      age:20,
      job:{
        type:'前端工程师',
        salary:'30K',
      },
      hobby:['抽烟','喝酒','烫头'],
    })


    // 方法
    function changeInfo(){
      person.name = '李四'
      person.age = 48
      person.job.type='后端工程师'
      person.job.salary='80K'
      person.hobby[0] = '学习'
      person.hobby[1] = '健身'
      person.hobby[2] = '社交'
      // console.log(name,age);
    }
    function addSex(){
      person.sex='男'
    }
    function deleteName(){
      delete person.name
    }
    // 返回一个对象(常用)
    return {
      person,
      changeInfo,
      addSex,
      deleteName
    }


  }
}
</script>

<style>

</style>
