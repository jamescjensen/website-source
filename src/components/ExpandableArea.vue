<template>
  <div class="column" v-bind="$attrs">
    <div @click="toggleExpansion">
      <span>
        <slot name="title" />
      </span>

      <span>
        <q-icon
          :size="iconSize"
          :name="expanded ? 'expand_more' : 'chevron_right'"
        />
      </span>
    </div>

    <div v-if="expanded">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const props = withDefaults(
  defineProps<{
    iconSize?: string;
    initialExpanded?: boolean;
  }>(),
  { iconSize: '14px', initialExpanded: true }
);

const expanded = ref<boolean>(props.initialExpanded);

function toggleExpansion() {
  expanded.value = !expanded.value;
}
</script>
