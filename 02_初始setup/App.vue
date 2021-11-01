<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ name }}</h2>
  <h2>年龄:{{ age }}</h2>
  <h2>性别：{{ sex }}</h2>
  <button @click="sayHello">说话（vue3所配置的sayHello）</button>
  <button @click="sayWelcome">说话（vue2所配置的sayWelcome）</button>
  <button @click="test1">测试一下在vue2的配置中去读取vue3中的数据和方法</button>
  <button @click="test2">
    测试一下在vue3的setup配置中去读取vue2中的数据和方法
  </button>
</template>

<script>
export default {
  data() {
    return {
      sex: '男',
    };
  },
  methods: {
    sayWelcome() {
      alert('欢迎来到尚硅谷学习');
    },
    test1() {
      console.log(this.sex);
      console.log(this.name);
      console.log(this.age);
      console.log(this.sayHello);
      this.sayHello(); //调用
    },
  },
  // 此处只是测试一下setup，暂时不考虑响应式的问题
  setup() {
    //  数据
    let name = '张三';
    let age = 18;

    //  方法
    function sayHello() {
      alert(`我叫${name},我${age}岁，你好啊！`);
    }
    function test2() {
      console.log(name);
      console.log(age);
      console.log(sayHello);
      // this.sayHello(); //调用
      console.log(this.sex);
      console.log(this.sayWelcome);
    }
    // 返回一个对象 常用
    return {
      name,
      age,
      sayHello,
      test2,
    };
    // 返回一个渲染函数
    //   return () => h('hi', '尚硅谷');
  },
};
</script>
