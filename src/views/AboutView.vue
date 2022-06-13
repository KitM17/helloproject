<template>
  <div>
    <div>
      <button @click="addLike">Like</button>
      <button @click="addDislike">Dislike</button>
    </div>
    <div class="like">Кол-во лайков: {{ likes }}</div>
    <div class="dislike">Кол-во дизлайков: {{ dislikes }}</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
    };
  },
  methods: {
    addLike() {
      this.likes += 1;
    },
    addDislike() {
      this.dislikes += 1;
    },
  },
};
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
.like {
  color: green;
}
.dislike {
  color: rebeccapurple;
}
</style>
