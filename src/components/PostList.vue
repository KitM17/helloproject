<template>
  <div class="post" v-for="post in posts">
    <div>Название: {{ post.title }}</div>
    <div>Описание: {{ post.body }}</div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
.post {
  padding: 2rem;
  border: 2px solid teal;
  margin-top: 2rem;
}
</style>