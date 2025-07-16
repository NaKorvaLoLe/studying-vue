<script>
import User from "./components/User.vue";

export default {
  components: {
    User,
  },
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
    deleteUser(index) {
      this.users.splice(index, 1);
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <input type="text" v-model="userName" placeholder="Имя" />
    <input type="email" v-model="userEmail" placeholder="E-mail" />
    <input type="password" v-model="userPass" placeholder="Пароль" />
    <p className="error">{{ error }}</p>
    <button class="btn" @click="sendData()">отправить</button>
    <div v-if="users.length == 0">Нет пользоаптелей</div>
    <div v-else-if="users.length == 1">1 gjkmpjfdfntkm</div>
    <div v-else>more 1 elem</div>
    <User
      v-for="(el, index) in users"
      :key="index"
      :user="el"
      :index="index"
      :deleteUser="deleteUser"
    />
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.wrapper input {
  border-radius: 10px;
  padding: 10px;
}
.btn {
  background-color: #00bb00;
  color: #fff;
  padding: 10px;
  border-radius: 5px;
  border: none;
  font-size: 16px;
}
</style>
