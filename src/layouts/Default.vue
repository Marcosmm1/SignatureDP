<template>
  <div>
    <v-navigation-drawer app v-model="drawer">
      <v-list nav dense>
        <v-list-item-group active-class="light-blue darken-1--text text--accent-4">
          <v-list-item v-for="(data, i) in drawerData " :key="i" :to="data.to" :class="active">
            <v-list-item-icon>
              <v-icon>{{data.icon}}</v-icon>
            </v-list-item-icon>
            <v-list-item-title>{{data.name}}</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <v-card class="mx-auto overflow-hidden">
      <v-app-bar height="45px" color="light-blue darken-4" dark app>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" x-large></v-app-bar-nav-icon>
        <v-toolbar-title class="empresa">Alfran Archipiélago</v-toolbar-title>
        <v-spacer></v-spacer>
      </v-app-bar>
      <v-content>
        <router-view></router-view>
      </v-content>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "Home",
  data: () => ({
    active: "active",
    drawerData: [
      {
        name: "Nuevo Cliente",
        icon: "mdi-newspaper-plus",
        to: "/newclient"
      },
      {
        name: "Nueva Proteccion",
        icon: "mdi-file-document-outline",
        to: "/newproteccion"
      },
      {
        name: "Clientes",
        icon: "mdi-store-outline",
        to: "/clients"
      },
      {
        name: "Salir",
        icon: "mdi-exit-to-app",
        to: "/"
      }
    ],
    drawer: false
  }),
  methods: {
    logout() {
      this.$router.push("/");
      localStorage.clear();
    }
  }
};
</script>

<style lang="scss" scoped>
.empresa {
  color: rgb(235, 41, 186);
  font-weight: 500;
  font-size: 40px;
}
.active {
  color: white;
}
</style>