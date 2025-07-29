<script>
import axios from "axios";
export default {
  data() {
    return {
      city: "",
      error: "",
      info: null,
    };
  },
  computed: {
    cityName() {
      return "«" + this.city + "»";
    },
    showTemp() {
      return " Температура: " + this.info.main.temp;
    },
    showFeelsLike() {
      return "Ощущается: " + this.info.main.feels_like;
    },
    showMinTemp() {
      return "Минимальная температура: " + this.info.main.temp_min;
    },
    showMaxTemp() {
      return "Минимальная температура: " + this.info.main.temp_max;
    },
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = "Название города слишком короткое";
        return false;
      }
      this.error = "";
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&lang=ru&appid=b26c945ad90494abf79f98ed7ce7584e`
        )
        .then((res) => (this.info = res.data))
        .catch((err) => (this.error = "Неверное название города"));
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
    <input type="text" name="" id="" placeholder="Ваш город" v-model="city" />
    <button :disabled="!city" @click="getWeather">Получить погоду</button>
    <p className="error" v-if="error">{{ error }}</p>
    <div v-if="info != null">
      <p>{{ showTemp }}</p>
      <p>{{ showMaxTemp }}</p>
      <p>{{ showMinTemp }}</p>
      <p>{{ showFeelsLike }}</p>
    </div>
  </div>
</template>

<style scoped>
.error {
  color: #ff7171;
}
.wrapper {
  width: 100%;
  max-width: 900px;
  border-radius: 10px;
  padding: 15px;
  background: #2c2c2c;
  text-align: center;
  color: #fff;
}
.wrapper h1 {
  margin-top: 20px;
}
.wrapper p {
  margin-top: 20px;
}
.wrapper input {
  margin-top: 20px;
  padding: 10px 15px;
  background: transparent;
  border: 2px solid #4e4e4e;
  color: #fff;
  border-radius: 5px;
  outline: none;
  width: 100%;
}
.wrapper input:focus {
  border: 2px solid #fff;
}
.wrapper button {
  margin-top: 20px;
  padding: 10px 15px;
  background: #e3bc4b;
  color: #fff;
  border-radius: 5px;
  border: 2px solid #e3bc4b;
  cursor: pointer;
  transition: transform 500ms ease;
}
.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
.wrapper button:disabled {
  background: #4e4e4e;
  cursor: not-allowed;
  border: 2px solid #4e4e4e;
}
.wrapper button:disabled:hover {
  transform: initial;
}
</style>
