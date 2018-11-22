<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin" :user="userData"></Editor>
  </div>
</template>

<script>
import Home from "./components/Home"
import Editor from "./components/Editor"

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
