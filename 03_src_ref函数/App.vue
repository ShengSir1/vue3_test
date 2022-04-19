<template>
  <!-- Vue3组件中的模板结构可以没有根标签 -->
  <h1>一个人的信息</h1>
  <h2>姓名：{{name}}</h2>
  <h2>年龄：{{age}}</h2>
  <h3>岗位：{{job.type}}</h3>
  <h3>薪资：{{job.salary}}</h3>
  <button @click="changeInfo">修改这个人的信息</button>
</template>

<script>
  import {ref} from 'vue' //引入ref函数
  export default {
  name: 'App',
  setup() {
    // 数据
    let name =ref('大帅逼')
    let age = ref(19)
    let job = ref({
      type:'前端工程师',
      salary:'30K',
    })
    // 方法
    function changeInfo(){
      name.value = '李四'
      age.value = 48
      job.value.type='后端工程师'
      job.value.salary='80K'
      // console.log(name,age);
    }

    // 返回一个对象(常用)
    return {
      name,
      age,
      changeInfo,
      job,
    }


  }
}
</script>

<style>

</style>
