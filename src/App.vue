<template>
  <div class="name">
    {{ name }}
  </div>
  <button
      class="btn btn-primary"
      v-on:click="updateName"
  >
    Click
  </button>
</template>

<script>

export default {
  setup() {
    let name = 'hobeom coder';

    const updateName = () => {
      name = 'change coder';
      console.log(name);
    };

    return {
      name,
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
