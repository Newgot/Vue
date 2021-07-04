<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <div class="app__btns">
      <my-button class="btn__create"
                 @click="showDialog">Создать пост
      </my-button>
      <my-select v-model="selectedSort"></my-select>
    </div>

    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"/>
    </my-dialog>

    <post-list :posts="posts"
               @remove="removePost"
               v-if="!isPostLoading"/>
    <div v-if="isPostLoading">Идёт загрзука...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import axios from 'axios';

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoading: false,
      selectedSort: ''
    };
  },
  methods: {
    createPost(post) {
      this.dialogVisible = false
      this.posts.push(post)
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5');
        this.posts = response.data
      } catch (e) {
        alert(e)
      }
      this.isPostLoading = false
    }
  },
  mounted() {
    this.fetchPosts()
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
}

.app {
  padding: 20px;
}

.btn__create {
  margin-top: 15px;
  margin-bottom: 15px;
}

.app__btns {
  display: flex;
  justify-content: space-between;
  margin-top: 15px;
  margin-bottom: 15px;
}
</style>
