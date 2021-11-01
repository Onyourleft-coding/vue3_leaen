<template>
  <h2>当前求和为:{{ sum }}</h2>
  <button @click="sum++">点我+1</button>
  <hr />
  <h2>当前的信息为：{{ message }}</h2>
  <button @click="message += '!'">修改信息</button>
</template>

<script>
import { ref, watch } from 'vue';
export default {
  name: 'demo',
  // vue2 watch写法
  //#region
  /*  watch: {
    // 监视sum 简写
    // sum(newValue, oldValue) {
    //   console.log('sum的值变化了', newValue, oldValue);
    // },

    // 完整写法 好处是可以配置很多选项
    sum: {
      immediate: true, //立即监视
      deep: true, //深度监视
      handler(newValue, oldValue) {
        console.log('sum的值变化了', newValue, oldValue);
      },
    },
  }, */
  //#endregion
  setup() {
    //  数据
    let sum = ref(0);
    let message = ref('你好啊');
    // watch 情况一：监视ref所定义的一个响应式数据
    /* watch(
      sum,
      (newValue, oldValue) => {
        console.log('sum的值变化了', newValue, oldValue);
      },
      { immediate: true }
    ); */

    // watch 情况二：监视ref所定义的多个响应式数据
    watch(
      [sum, message],
      (newValue, oldValue) => {
        console.log('sum或msg变化了', newValue, oldValue);
      },
      { immediate: true }
    );
    // 返回一个对象 常用
    return {
      sum,
      message,
    };
  },
};
</script>
