<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      dark
      app
      class="grey--text text--lighten-2"
    >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            INSPIRE
          </v-list-item-title>
          <v-list-item-subtitle color="blue">
            todo list
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" link :to="item.to">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app dark class="grey--text text--lighten-1">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application | Todo list</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    items: [
      { title: "Dashboard", icon: "mdi-format-list-checks", to: "/" },
      { title: "About", icon: "mdi-help-box", to: "/about" },
    ],

    drawer: false,
  }),
};
</script>
<style lang="scss">
#inspire {
  background: url("./assets/img/backg.webp");
  background-size: cover;
}
</style>
