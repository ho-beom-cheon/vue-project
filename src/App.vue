<template>
  <div :class="nameClass">
    {{ name }}
  </div>
  <!--  'v-bind:' 는 ':' 로 생략가능-->
  <input :type="type" :value="name">
  <!--  'v-on:' 는 '@' 로 생략가능-->
  <button
      class="btn btn-primary"
      @click="updateName"
  >
    Click
  </button>
</template>

<script>
// 템플릿에서도 동시에 값이 변경되기위해 추가해야함
import { ref } from 'vue';       // ref : 기본자료형
import { reactive } from 'vue';  // reactive : Object, Array

export default {
  setup() {
    const name = ref('hobeom coder');
    const type = ref('number');
    const nameClass = ref('');
    const name2 = reactive({
      id : 1
    });

    const updateName = () => {
      //
      name.value = 'change coder';   // ref를 사용할 때는 name.value 형태로 사용
      type.value = 'text';
      nameClass.value = 'name';
      name2.id = 2;                  // 안에 들어있는 값을 바로 접근 가능
      console.log(name);
    };

    return {
      name,
      type,
      nameClass,
      name2,
      updateName,
    };
  }
}
</script>

<style>
.name {
  color: red;
}
</style>
