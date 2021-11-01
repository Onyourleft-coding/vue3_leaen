<template>
  <h1>一个人的信息</h1>
  姓：<input type="text" v-model="person.firstName" />
  <br />
  名：<input type="text" v-model="person.lastName" />
  <br />
  <span> 全名：{{ person.fullName }} </span>
  <br />
  全名2：<input type="text" v-model="person.fullName" />
</template>

<script>
import { reactive, computed } from 'vue';
export default {
  name: 'demo',
  //不建议写
  /* computed: {
    // 简写得写成函数形式
    fullName() {
      return this.person.firstName + '-' + this.person.lastName;
    },
  }, */
  setup() {
    //  数据
    let person = reactive({
      firstName: '张',
      lastName: '三',
      age: 18,
    });
    // vue3写法 computed组合式api 简写形式（没有考虑计算属性被修改的情况）
    //计算属性 传入一个回调函数，普通/箭头都可以
    // 这里思考一个问题，名字这种应该是人的属性，不应该单独伶出去
    // 所以我们不用 let fullName的形式
    // 直接在person上追加一个fullName属性
    /*  person.fullName = computed(() => {
      return person.firstName + '-' + person.lastName;
    }); */

    // 计算属性完整写法（考虑读和写）
    person.fullName = computed({
      get() {
        return person.firstName + '-' + person.lastName;
      },
      set(value) {
        const nameArr = value.split('-');
        console.log(nameArr);
        person.firstName = nameArr[0];
        person.lastName = nameArr[1];
      },
    });

    // 返回一个对象 常用
    return {
      person,
      // fullName,
    };
  },
};
</script>
