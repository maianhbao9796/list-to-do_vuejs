<template>
  <div class="home-screen">
    <img
      alt="logo"
      src="https://raw.githubusercontent.com/mustafaynk/todolist/master/appgallery/logo.png"
    />
    <button class="home-screen__btn" @click="onRunApp">Run App</button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },

  methods: {
    onRunApp() {
      this.$emit('on-run-app');
    },
  },
};
</script>

<style lang="scss" scoped>
.home-screen {
  display: flex;
  flex-direction: column;
  align-items: center;

  &__btn {
    height: 50px;
    width: 200px;
    padding: 10px;
    font-size: 20px;
    font-weight: bold;
    color: rgb(28, 145, 255);
    cursor: pointer;
    border-radius: 30px;
    border: none;
    box-shadow: 1px 1px 10px 5px rgb(0, 0, 0, 0.2);
  }
}
</style>
