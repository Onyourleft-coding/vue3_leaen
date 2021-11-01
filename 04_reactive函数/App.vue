<template>
  <h1>一个人的信息</h1>
  <h2 v-show="person.name">姓名：{{ person.name }}</h2>
  <h3>年龄:{{ person.age }}</h3>
  <h3 v-show="person.sex">性别：{{ person.sex }}</h3>
  <h2>工作种类：{{ person.job.type }}</h2>
  <h2>工作薪水：{{ person.job.salary }}</h2>
  <h2>爱好：{{ person.hobby }}</h2>
  <h3>测试的数据C:{{ person.a.b.c }}</h3>
  <button @click="changeInfo">修改人的信息</button>
  <button @click="addSex">添加一个sex属性</button>
  <button @click="deleteName">删除一个name属性</button>
</template>

<script>
import { reactive } from 'vue';
export default {
  setup() {
    //  数据
    let person = reactive({
      name: '张三',
      age: 18,
      hobby: ['抽烟', '喝酒', '烫头'],
      job: { type: '前端工程师', salary: '30K' },
      a: {
        b: {
          c: 666,
        },
      },
    });
    // 方法
    function changeInfo() {
      person.name = '李四';
      person.age = 48;
      person.job.type = '全栈工程师';
      person.job.salary = '60k';
      person.a.b.c = 999;
      person.hobby[0] = '学习';
    }
    function addSex() {
      person.sex = '男';
    }
    function deleteName() {
      delete person.name;
    }
    // 返回一个对象 常用
    return {
      person,
      changeInfo,
      addSex,
      deleteName,
    };
    // 返回一个渲染函数
    //   return () => h('hi', '尚硅谷');
  },
};
</script>
