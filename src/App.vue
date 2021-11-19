<template>
  <input
      type="text"
      v-model="name"
  >
  <button
      class="btn btn-primary"
      @click="onSubmit"
  >
    Click
  </button>
</template>

<script>
// 템플릿에서도 동시에 값이 변경되기위해 추가해야함
import { ref } from 'vue';       // ref : 기본자료형

export default {
  setup() {
    const name = ref('hobeom coder');

    const onSubmit = () => {
      console.log(name.value);
    }

    return {
      name,
      onSubmit,
    };
  }
}
</script>

<style>
.name {
  color: red;
}
</style>
