<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li class="nav-item">
            <router-link class="nav-link" :to="{name:'Home'}" exact>
              <img class="logo" src="./assets/build-a-bot-logo.png" alt>
              Build-A-Bot
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{name:'Build'}" exact>Build</router-link>
          </li>
          <li class="nav-item">
          <router-link class="nav-link" :to="{name:'BrowseParts'}" exact>Browse Parts</router-link>
          </li>
          <li class="nav-item cart">
          <router-link class="nav-link" :to="{name:'Cart'}" exact>Cart</router-link>
          <div class="cart-items">
            {{cart.length}}
          </div>
          </li>
        </ul>
      </nav>
    </header>
    <div class="container">
      <aside class="aside">
        <router-view name="sidebar"/>
      </aside>
      <main>
        <router-view/>
      </main>
    </div>
  </div>
</template>

<script>
// import HomePage from './home/HomePage.vue';
// import RobotBuilder from './build/RobotBuilder.vue';

import { mapState, mapGetters } from 'vuex';

export default {
  name: 'app',
  components: {
    // HomePage,
    // RobotBuilder,
  },
  computed: {
    cart() {
      return this.$store.state.robots.cart;
    },
    ...mapState({ rootFoo: 'foo', robotsFoo: state => state.robots.foo }),
    // rootFoo() {
    //   return this.$store.state.foo;
    // },
    // robotsFoo() {
    //   return this.$store.state.robots.foo;
    // },
    ...mapState('users', { usersFoo: 'foo' }),
    // usersFoo() {
    //   return this.$store.state.users.foo;
    // },

    ...mapGetters({ rootGetterFoo: 'foo' }),
    // rootGetterFoo() {
    //   return this.$store.getters.foo;
    // },

    ...mapGetters('users', { usersGetterFoo: 'foo' }),
    ...mapGetters('robots', { robotsGetterFoo: 'foo' }),

    // usersGetterFoo() {
    //   return this.$store.getters['users/foo'];
    // },
    // robotsGetterFoo() {
    //   return this.$store.getters['robots/foo'];
    // },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  background: linear-gradient(to bottom, #555, #999);
  background-attachment: fixed;
}
</style>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
main {
  /* margin: 0 auto; */
  padding: 3px;
  background-color: white;
  width: 964px;
  min-height: 300px;
}
header {
  background-color: #999;
  width: 1114px;
  margin: 0 auto;
}
ul {
  padding: 3px;
  display: flex;
}
.nav-item {
  display: inline-block;
  padding: 5px 10px;
  font-size: 22px;
  border-right: 1px solid #bbb;
}
.nav-item.cart{
  position: relative;
  margin-left:auto;
  border-right:none;
}
.logo {
  vertical-align: middle;
  height: 30px;
}
.nav-link {
  text-decoration: none;
  color: inherit;
}
.router-link-active {
  color: white;
}
.container {
  display: flex;
  margin: 10px auto 0 auto;
  justify-content: center;
}
.aside {
  padding: 30px;
  background-color: #aaa;
  width: 150px;
  min-height: 300px;
}
.cart-items{
  position:absolute;
  top:-5px;
  right: -9px;
  font-size:18px;
  display: inline-block;
  width:20px;
  text-align:center;
  border-radius:100px;
  background-color:mediumseagreen;

}
</style>
