<template>
  <q-layout view="hHh Lpr lFf">
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

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered :width="250">
      <div class="column justify-between" style="height: 100%">
        <q-list class="col-auto">
          <sidebar-link
            v-for="link in sections"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
        <q-list class="col-auto">
          <q-separator spaced />
          <q-item-label header> External Links </q-item-label>

          <sidebar-link
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
      </div>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer bordered class="bg-grey-3 text-primary">
      <div class="row q-col-gutter-md justify-between q-pa-sm">
        <a href="https://github.com/jamescjensen/website-source">Source</a>
        <a href="https://commitmono.com/">Font: CommitMono</a>
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import SidebarLink, { SidebarLinkProps } from 'components/SidebarLink.vue';

const sections: SidebarLinkProps[] = [
  {
    title: 'Skills',
    external: false,
    internalPath: { path: '/', hash: '#skill-section' },
  },
  {
    title: 'Jobs',
    external: false,
    internalPath: { path: '/', hash: '#job-section' },
  },
];

const essentialLinks: SidebarLinkProps[] = [
  {
    title: 'Email',
    caption: 'jcjens94@gmail.com',
    icon: 'mail',
    link: 'mailto:jcjens94@gmail.com',
    external: true,
  },
  {
    title: 'Github',
    caption: 'github.com/jamescjensen',
    icon: 'code',
    link: 'https://github.com/jamescjensen',
    external: true,
  },
  {
    title: 'Instagram',
    caption: '@jackjensenofficial',
    icon: 'public',
    link: 'https://instagram.com/jackjensenofficial',
    external: true,
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
