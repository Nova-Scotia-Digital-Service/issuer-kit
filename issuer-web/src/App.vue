<template>
  <v-app>
    <Header />    
    <v-main>
      <h1>Issuer Name</h1>
      <router-view></router-view>
    </v-main>

    <Footer />
  </v-app>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #408334;
    }
  }
}

//CNS style
.underLineLink {
  text-decoration: underline;
}
</style>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";

export default {
  name: "app",
  components: {
    Header,
    Footer
  },
  data() {
    return {};
  }
};
</script>
