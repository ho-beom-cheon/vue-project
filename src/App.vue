<template>
<!--  <div v-if="toggle">true</div>
  <div v-else>false</div>
  <button @click="onToggle">Toggle</button>-->

  <div class="container">
    <h2>To-Do List</h2>
    <form @submit.prevent="onSubmit">
      <div class="d-flex">
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
      </div>
      <div v-show="hasError" style="color : red">
        This field cannot be empty
      </div>
    </form>

    <div
        v-for="todo in todos"
        :key="todo.id"
        class="card mt-2"
    >
      <div class="card-body p-2">
        {{ todo.subject }}
      </div>
    </div>

  </div>
</template>

<script>
// 템플릿에서도 동시에 값이 변경되기위해 추가해야함
import { ref } from 'vue';       // ref : 기본자료형

export default {
  setup() {
    const toggle = ref(false);
    const todo = ref('');
    const todos = ref([
      {id: 1, subject: '휴대폰 사기'},
      {id: 2, subject: '장보기'}
    ]);
    const hasError = ref(false);

    const onSubmit = () => {
      //e.preventDefault();  // submit 새로고침 방지
      if (todo.value === '') {
        hasError.value = true;
      } else {
        todos.value.push({
          id: Date.now(),
          subject: todo.value
        })
        hasError.value = false;
      }
    }
    const onToggle = () => {
      toggle.value = !toggle.value
    }

    return {
      todo,
      toggle,
      todos,
      hasError,
      onSubmit,
      onToggle,
    };
  }
}
</script>

<style>

</style>
