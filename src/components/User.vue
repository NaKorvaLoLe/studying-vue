<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    deleteUser: {
      type: Function,
      required: true,
    },
  },
};
</script>
<template>
  <div className="user">
    <span>{{ user.name }}</span> | <span>{{ user.email }}</span> |
    <span>{{ user.pass }}</span>
    <button className="danger" @click="deleteUser(index)">удалить</button>
  </div>
</template>
<style scoped>
.user {
  background-color: antiquewhite;
  border-radius: 10px;
  padding: 15px;
  display: flex;
  gap: 10px;
}
.danger {
  background-color: red;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
}
</style>
