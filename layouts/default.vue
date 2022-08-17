<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      color="#073b5b"
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-menu
        offset-y
      >
        <template v-slot:activator="on, attrs">
          <v-btn
            color="#073b5b"
            height="100%"
            v-bind="on"
            v-on="attrs"
            elevation="0"
          >
            <v-icon
              color="white"
            >
              mdi-bell
            </v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(notificatio, index) in Notification"
            :key="index"
          >
            <v-list-item-title>{{notificatio.title}}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-menu
        open-on-hover
        offset-y
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="#073b5b"
            height="100%"
            v-bind="attrs"
            v-on="on"
            elevation="0"
          >
          <v-row>
            <v-col>
              <v-avatar
                size="40"
              >
                <v-img
                  src="https://img.freepik.com/fotos-gratis/imagem-aproximada-em-tons-de-cinza-de-uma-aguia-careca-americana-em-um-fundo-escuro_181624-31795.jpg?w=2000"
                >
                </v-img>
              </v-avatar>
            </v-col>
            <v-col>
              <p style="color:white; margin-top: 10%;">
                  Bernardo
              </p>
            </v-col>
          </v-row>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, index) in items2"
            :key="index"
            link
            :to="item.link"
          >
            <v-list-item-title>{{item.title}}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      Notification: [
        {title: 'socorro', data: 'Muito frio todays'}
      ],
      items2: [
        {title: 'Meus dados',link: "google.com"},
        {title: 'Sair', link: "google.com"}
        
      ],
      items: [
        {
          icon: 'mdi-book',
          title: 'Create',
          to: '/create'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'UNOCHAPECO'
    }
  }
}
</script>
