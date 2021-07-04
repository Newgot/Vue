<template>
  <div class="empty">
    <p><slot></slot> не найден</p>
  </div>
</template>
<script>
export default {
  name: 'my-empty'
}
</script>

<style scoped>
.empty {
  padding: 10px 15px;
  color: teal;
  background: none;
  border: 1px solid darkred;
}
.empty{
  font-weight: 600;
  margin-top: 15px;
  margin-bottom: 15px;
}


</style>