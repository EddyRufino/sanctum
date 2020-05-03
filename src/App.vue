<template>
<div id="app">
  <v-app>
    <v-content>
      <router-view />
    </v-content>
    <v-app-bar app color="primary">
      <div class="d-flex align-center">
        <v-btn @click.stop="drawer = !drawer" color="primary" elevation="0">
          <v-icon>reorder</v-icon>
        </v-btn>
      </div>

      <v-spacer></v-spacer>

      <!-- <router-link to="/about">About</router-link>    -->

      <template v-if="$store.state.auth">
        <span class="color-user-nav">{{ $store.state.user.name }}</span>
        <!-- <button @click="logout">Logout</button> -->
      </template>
      
      <template v-else>
        <v-btn color="primary" elevation="0">
          <router-link  to="/login">Login</router-link>
        </v-btn>

        <v-btn color="primary" elevation="0">
          <router-link  to="/register">Register</router-link>
        </v-btn>
      </template>
    </v-app-bar>

    <!-- Drawer -->
    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <template v-if="$store.state.auth">
        <v-list-item>
          <v-list-item-avatar>
            <v-img src="https://randomuser.me/api/portraits/men/78.jpg"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>{{ $store.state.user.name }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </template>

      <v-divider></v-divider>

      <v-list dense>

        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title @click="$router.push({ name:`${item.route}` })">{{ item.title }}</v-list-item-title>
          </v-list-item-content>

        </v-list-item>


        <v-list-item  class="mano-drawer" v-if="$store.state.auth">
          <v-list-item-icon>
            <v-icon>home</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title @click="logout">
              Logout
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>

      </v-list>
    </v-navigation-drawer>

    <!-- <v-content>
      <HelloWorld />
    </v-content> -->
  </v-app>
</div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  data () {
    return {
      drawer: null,
      items: [
        { title: 'Home', icon: 'dashboard', route: 'Home' },
        { title: 'About', icon: 'question_answer', route: 'About' },
      ],
    }
  },
  methods: {
    async logout() {
      await this.$store.dispatch("logout");
      return this.$router.push("/login");
    }
  },
};
</script>

<style lang="scss">
a {
  color: white !important;
  text-decoration: none;
}
.mano-drawer {
  cursor: pointer;

  &:hover {
    background-color: #c1c1c1 !important;
  }
}
.color-user-nav {
  color: rgba(255, 255, 255, 1) !important;
  cursor: pointer;
}
</style>