<script>
export default {
  data() {
    return {
      title: "Hello World",
      content:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nemo similique mollitia aperiam quo veniam labore inventore quos commodi dignissimos ex iusto architecto aspernatur unde, obcaecati quisquam aliquid sed excepturi ea.",
    };
  },
  methods: {
    send(word) {
      this.title = "new title";
      this.content = word;
    },
  },
};
</script>

<template>
  <h3>{{ title }}</h3>
  <p>{{ content }}</p>
  <button type="button" @click="send('some text')">Send</button>
</template>

<style scoped>
h3 {
  font-weight: 600;
}
p {
  color: #b398ff;
}
</style>
