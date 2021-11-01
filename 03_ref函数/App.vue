<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ name }}</h2>
  <h3>年龄:{{ age }}</h3>
  <h2>工作种类：{{ job.type }}</h2>
  <h2>工作薪水：{{ job.salary }}</h2>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { ref } from 'vue';
export default {
  // 此处只是测试一下setup，暂时不考虑响应式的问题
  setup() {
    //  数据
    let name = ref('张三');
    let age = ref(18);
    let job = ref({
      type: '前端工程师',
      salary: '30K',
    });
    //  方法
    function sayHello() {
      alert(`我叫${name},我${age}岁，你好啊！`);
    }
    function changeInfo() {
      name.value = '李四';
      age.value = 48;
      // console.log(job.value);
      job.value.type = '全栈工程师';
      job.value.salary = '60k';

      // console.log(name, age);
    }
    // 返回一个对象 常用
    return {
      name,
      age,
      job,
      sayHello,
      changeInfo,
    };
    // 返回一个渲染函数
    //   return () => h('hi', '尚硅谷');
  },
};
</script>
