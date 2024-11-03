<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Knjiznica
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

defineOptions({
  name: 'MainLayout'
})

const linksList = [
  {
    title: 'Pocetna',
    caption: 'Pocetna stranica',
    icon: 'home',
    link: '#/'
  },
  {
    title: 'Popis knjiga',
    caption: 'Popis svih knjiga u knjiznici',
    icon: 'book',
    link: '#/popis_knjiga'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'O nama',
    caption: 'O nama',
    icon: '',
    link: '#/ONamaPage'
  },
  {
    title: 'lokacija',
    caption: 'lokacija',
    icon: '',
    link: '#/lokacija '
  },
  {
    title: 'Login',
    caption: 'Login',
    icon: '',
    link: '#/login '
  },
  {
    title: 'registracija',
    caption: 'Community Quasar projects',
    icon: '',
    link: '#/registracija '
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
