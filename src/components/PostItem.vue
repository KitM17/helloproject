<template>
  <div class="post">
    <div>
      <div> {{post.id}}</div>
      <div>Название: {{ post.title }}</div>
      <div>Описание: {{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button @click="$emit('remove', post)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
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
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>