<template>
  <q-page class="column items-center q-pa-md">
    <div ref="containerDiv" :style="containerStyle">
      <div class="row items-baseline full-width q-col-gutter-md">
        <div class="col-12">
          <my-skills class="q-pb-md" id="skill-section" />
          <my-jobs class="q-pb-md" id="job-section" />
        </div>
      </div>
    </div>

    <q-page-sticky
      v-if="showWidthFab"
      position="bottom-right"
      :offset="[18, 18]"
    >
      <q-btn
        dense
        fab
        :icon="useFullWidth ? 'width_full' : 'width_normal'"
        color="accent"
        @click="toggleFullWidth"
      />
    </q-page-sticky>
  </q-page>
</template>

<script setup lang="ts">
import { useQuasar } from 'quasar';
import { HTMLAttributes, computed, ref } from 'vue';

import MySkills from './index-sections/MySkills.vue';
import MyJobs from './index-sections/MyJobs.vue';

const $q = useQuasar();

const containerDiv = ref<HTMLElement>();

const useFullWidth = ref<boolean>(false);

const showWidthFab = computed<boolean>(() => {
  return $q.screen.width >= 1250;
});

const containerStyle = computed<HTMLAttributes['style']>(() => {
  if (useFullWidth.value) {
    return {
      width: '100%',
    };
  } else {
    return {
      width: '100%',
      'max-width': '1000px',
    };
  }
});

function toggleFullWidth() {
  useFullWidth.value = !useFullWidth.value;
}
</script>
