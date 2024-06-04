<template>
  <div class="app">
    <my-button @click="this.dialogVisible = true">Create post</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import MyDialog from "./components/UI/MyDialog.vue";

export default {
  components: {
    PostForm,
    PostList,
    MyDialog,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "VueJS", body: "Cool framework" },
        { id: 2, title: "ReactJS", body: "Cool library" },
        { id: 3, title: "NestJS", body: "Cool backend" },
      ],
      dialogVisible: false,
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
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>
