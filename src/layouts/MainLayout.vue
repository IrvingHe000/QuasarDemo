<template>
  <q-layout view="hHh LpR fFf">
    <q-header elevated>
      <q-toolbar> 

        <q-toolbar-title class="absolute-center"> Quasar App </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-footer>
      <q-tabs>
      <q-route-tab v-for="nav in navs"
          :key="nav.key"
          :to="nav.to" 
          :icon="nav.icon"
          :label="nav.label"/>
      </q-tabs>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767"
      :width="250"
      show-if-above
      bordered
      content-class="bg-primary"
    >
      <q-list dark>
        <q-item-label header> Navbar </q-item-label>
        <q-item 
          
          v-for="nav in navs"
          :key="nav.key"
          :to="nav.to" 
          class="text-grey-4"
          exact
          clickable>
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>

          <q-item-section avatar>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>

        </q-item>

  
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from "quasar";

export default {
  name: "MainLayout",
  props: {
    title: {
      type: String,
      required: true,
    },

    caption: {
      type: String,
      default: "",
    },

    link: {
      type: String,
      default: "#",
    },

    icon: {
      type: String,
      default: "",
    },
  },

  data() {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      navs: [
        {label: 'Todo',
          icon: 'list',
          to: '/pagetodo',
          key: '1'
        },
        {label: 'Settings',
          icon: 'settings',
          to: '/setting',
          key: '2'
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  @media screen and (min-width: 768px) {
    .q-footer {
      display: none;
    } 
    }

    .q-drawer .q-router-link--exact-active {
      color: white !important;
      }
</style>