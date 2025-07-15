<template>
  <div class="container">
    <label class="title">below from api .net9 : </label>
    <br>
    <label class="message">{{ message }}</label>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      message: 'Loading...',
    };
  },
  mounted() {
    fetch('https://www.irohani-tech.jp/api/message')
      .then(response => response.text())
      .then(data => {
        this.message = data;
      })
      .catch(error => {
        console.error('API Error:', error);
        this.message = 'Failed to load message';
      });
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.title {
  font-size: 48px;
  font-weight: bold;
}
.message {
  font-size: 24px;
  font-weight: bold;
}
</style>
