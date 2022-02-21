<template>
  <div class="app">
    <HomeScreen v-if="!isRunning" @on-run-app="onHandleRunApp" />
    <InteractScreen v-else />
  </div>
</template>

<script>
import HomeScreen from "@/components/HomeScreen.vue";
import InteractScreen from "@/components/InteractScreen.vue";

export default {
  name: 'App',
  components: {
    HomeScreen,
    InteractScreen
  },

  data() {
    return {
      isRunning: false,
    }
  },

  methods: {
    onHandleRunApp() {
      this.isRunning = !this.isRunning;
    }
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }
  .app {
    width: 100%;
    height: 1000px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    background-image: url("https://toigingiuvedep.vn/wp-content/uploads/2021/02/background-may-dep-cho-khai-giang-820x547.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    img {
      border-shadow: 1px 1px rgb(0,0,0,0.2);
      margin: 60px 0;
      height: 300px;
      width: auto;
    }
  }

</style>
