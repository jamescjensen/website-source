<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="text-center">
          James (Jack) Jensen
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer bordered>
      <div class="row q-col-gutter-md justify-between q-pa-md">
        <q-space />
        <a href="https://www.linkedin.com/in/james-c-jensen" target="_blank">
          LinkedIn
        </a>
        <a href="https://github.com/jamescjensen" target="_blank">GitHub</a>
        <q-space />
        <a href="mailto:jcjens94@gmail.com">jcjens94@gmail.com</a>
        <q-space />
        <a
          href="https://github.com/jamescjensen/website-source"
          target="_blank"
        >
          Source
        </a>
        <a href="https://commitmono.com/" target="_blank">Font: CommitMono</a>
        <q-space />
      </div>
    </q-footer>
  </q-layout>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
a:link {
  color: #99c8ff;
}

a:visited {
  color: #61a9ff;
}
</style>
