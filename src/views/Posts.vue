<template>
  <div class="app">
    <h1>Страница с постами</h1>

    <my-button @click="showDialog" style="margin: 15px">
      Создать пост</my-button
    >
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"
    /></my-dialog>

    <post-list :posts="posts" @remove="removePost" v-if="!isPostsLoading" />
    <div v-else>Идёт загрузка...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "../components/ui/MyButton.vue";
import axios from "axios";
export default {
  components: {
    PostList,
    PostForm,
    MyButton,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        setTimeout(async () => {
          const responce = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=10"
          );
          this.posts = responce.data;
            this.isPostsLoading=false;
        }, 1000);
      } catch (e) {
        alert("Ошибка");
      } finally {
      
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
.app {
  pad: 2.5rem;
}
</style>