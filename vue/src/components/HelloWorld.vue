<template>
  <div @click="testFn">
    hello
  </div>
</template>

<script>
  export default {
    data: () => ({
    }),

    methods: {
      testFn() {
        alert("ll")
      }
    },
  }
</script>