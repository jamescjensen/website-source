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
      <div class="row q-col-gutter-md justify-around q-pa-md">
        <a
          class="col-auto"
          href="https://www.linkedin.com/in/james-c-jensen"
          target="_blank"
        >
          LinkedIn
        </a>
        <a
          class="col-auto"
          href="https://github.com/jamescjensen"
          target="_blank"
        >
          GitHub
        </a>
        <a class="col-auto" href="mailto:jcjens94@gmail.com">
          jcjens94@gmail.com
        </a>
        <a class="col-auto" href="resume.pdf" target="_blank"> Resume </a>
        <a
          class="col-auto"
          href="https://github.com/jamescjensen/website-source"
          target="_blank"
        >
          Source
        </a>
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
