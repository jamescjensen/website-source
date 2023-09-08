<template>
  <q-item
    clickable
    :tag="external ? 'a' : 'div'"
    target="_blank"
    :href="link"
    :to="internalPath"
  >
    <q-item-section v-if="icon" avatar>
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>{{ caption }}</q-item-label>
    </q-item-section>
  </q-item>
</template>

<script setup lang="ts">
export interface SidebarLinkProps {
  title: string;
  caption?: string;
  link?: string;
  icon?: string;
  internalPath?: string | object;
  external: boolean;
}
withDefaults(defineProps<SidebarLinkProps>(), {
  caption: '',
  icon: '',
});
</script>
