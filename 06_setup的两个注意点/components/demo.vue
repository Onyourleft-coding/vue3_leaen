<template>
  <h1>一个人的信息</h1>
  <h2>姓名：{{ person.name }}</h2>
  <h3>年龄:{{ person.age }}</h3>
  <button @click="test">测试出发一下Demo组件的Hello事件</button>
  <slot></slot>
</template>

<script>
import { reactive } from 'vue';
export default {
  name: 'demo',
  props: ['msg', 'daylitime'], //声明接受父组件传递过来的props
  emits: ['hello'],
  setup(props, context) {
    // console.log('------setup', props);
    // console.log('------setup', context.attrs); //context本质上是一个对象 像与vue2中的$attrs，捡漏选手，没有声明接受的props将到里面去，但v3会警告
    // console.log('-----setup', context.emit); //触发自定义事件

    console.log('----setup', context.slots); //插槽
    //  数据
    let person = reactive({
      name: '张三',
      age: 18,
    });
    // 方法
    function test() {
      context.emit('hello', 666);
    }
    // 返回一个对象 常用
    return {
      person,
      test,
    };
  },
};
</script>
