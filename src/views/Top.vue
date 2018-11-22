<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin" :user="userData"></Editor>
    <router-link :to="{name : 'terms'}">利用規約</router-link>
  </div>
</template>

<script>
import Home from "../components/Home"
import Editor from "../components/Editor"

export default {
  name: 'app',
  data () {
    return {
      isLogin: false,
      userData: null
    }
  },
  created() {
    firebase.auth().onAuthStateChanged(user => {
      this.isLogin = user != null
      this.userData = user
    })
  },
  components: {
    Home: Home,
    Editor: Editor
  }
}
</script>

<style lang="scss">
#top {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
</style>