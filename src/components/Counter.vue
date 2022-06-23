<template>
  {{ counter }}
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
    };
  },
  mounted() {
    setInterval(() => {
      this.counter++;
    }, 100);
  },
};
</script>