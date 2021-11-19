<template>
  <div class="container">
    <h2>To-Do List</h2>
    <form
        @submit.prevent="onSubmit"
        class="d-flex"
    >
      <div class="flex-grow-1">
        <input
            class="form-control"
            type="text"
            v-model="todo"
            placeholder="Type new to-do"
        >
      </div>
      <div class="mx-2">
        <button
            class="btn btn-primary"
            type="submit"
        >
          Add
        </button>
      </div>
    </form>
    {{ todos }}
  </div>
</template>

<script>
// 템플릿에서도 동시에 값이 변경되기위해 추가해야함
import { ref } from 'vue';       // ref : 기본자료형

export default {
  data() {
    const todo = ref('');
    const todos = ref([]);

    const onSubmit = () => {
      //e.preventDefault();  // submit 새로고침 방지
      todos.value.push({
        id : Date.now(),
        subject : todo.value
      })
    }

    return {
      todo,
      todos,
      onSubmit,
    };
  }
}
</script>

<style>

</style>
