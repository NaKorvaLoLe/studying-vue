<script>
export default {
  data() {
    return {
      users: [],
      error: "",
      userName: "",
      userEmail: "",
      userPass: "",
    };
  },
  methods: {
    sendData() {
      if (this.userName == "") {
        this.error = "Введите имя";
        return;
      } else if (this.userEmail == "") {
        this.error = "Введите e-mail";
        return;
      } else if (this.userPass == "") {
        this.error = "Введите пароль";
        return;
      }
      this.error = "";
      this.users.push({
        name: this.userName,
        email: this.userEmail,
        pass: this.userPass,
      });
    },
  },
};
</script>

<template>
  <input type="text" v-model="userName" placeholder="Имя" />
  <input type="email" v-model="userEmail" placeholder="E-mail" />
  <input type="password" v-model="userPass" placeholder="Пароль" />
  <p className="error">{{ error }}</p>
  <button @click="sendData()">отправить</button>
  <div v-if="users.length == 0">Нет пользоаптелей</div>
  <div v-else-if="users.length == 1">1 gjkmpjfdfntkm</div>
  <div v-else>more 1 elem</div>
  <div v-for="(el, index) in users" :key="index">
    <span>{{ el.name }}</span> | <span>{{ el.email }}</span> |
    <span>{{ el.pass }}</span>
  </div>
</template>

<style scoped></style>
