<template>
  <div class="post">
    <div class="">
      <p><strong>Название: </strong>{{ post.title }}</p>
      <p><strong>Оисание: </strong>{{ post.body }}</p>
    </div>
    <div class="post_btns">
      <my-button>Удалить</my-button>
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

<style scoped>
.post {
  padding: 15px;
  margin-top: 15px;
  border: 2px solid teal;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>