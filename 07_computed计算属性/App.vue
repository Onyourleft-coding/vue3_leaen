<template>
  <demo />
</template>

<script>
import demo from './components/demo.vue';
export default {
  name: 'App',
  components: {
    demo,
  },
  setup() {
    function showHelloMsg(value) {
      alert(`你好啊，你触发了hello事件，我收到的参数是:${value}`);
    }
    return {
      showHelloMsg,
    };
  },
};
</script>
