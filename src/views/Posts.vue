<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <input
        v-bind:value="title"
        @input="title=$event.target.value"
        class="input"
        type="text"
        placeholder="Название"
      />
      <input
        v-bind:value="body"
          @input="body=$event.target.value"
        class="input"
        type="text"
        placeholder="Описание"
      />
      <button class="btn" @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div>Название: {{ post.title }}</div>
      <div>Описание: {{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "JavaScript", body: "Описание поста" },
        { id: 2, title: "JavaScript 2", body: "Описание поста 2" },
        { id: 3, title: "JavaScript 3", body: "Описание поста 3" },
        { id: 4, title: "JavaScript 4", body: "Описание поста 4" },
      ],
      title: "",
      body: "",
    };
  },
  methods: {
    createPost() {
      const newPost={
        id: Date.now(),
        title:this.title,
        body: this.body,
      }
      this.posts.push(newPost);
      this.title="";
      this.body="";
    },
 },
  
};
</script>

<style>
.app {
  pad: 2.5rem;
}
.post {
  padding: 2rem;
  border: 2px solid teal;
  margin-top: 2rem;
}
form {
  display: flex;
  flex-direction: column;
}
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 1rem;
}
.btn {
  margin-top: 1rem;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>