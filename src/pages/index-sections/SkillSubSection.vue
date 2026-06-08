<template>
  <expandable-area icon-size="18px">
    <template #title>
      <span class="text-title-subsection"> Skills </span>
    </template>
    <div class="row q-col-gutter-sm">
      <div class="col-12">
        <div class="text-title-subsubsection">
          {{ 'Recent' }}
        </div>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in recentSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </div>
      <div class="col-12">
        <div class="text-title-subsubsection">
          {{ 'Previously Used' }}
        </div>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in previouslyUsed" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </div>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import ExpandableArea from 'components/ExpandableArea.vue';

const recentSkills = [
  'Go',
  'AWS',
  'Kubernetes',
  'Protobuf',
  'Postgres',
  'TimescaleDB',
  'JavaScript',
  'TypeScript',
  'Node.js',
];

const previouslyUsed = [
  'HTML',
  'CSS',
  'Google Cloud',
  'Quasar',
  'Vue',
  'React',
  'Perl',
  'C',
  'C++',
  'C#',
  'Unity',
  'Flutter / Dart',
  'Capacitor',
  'PHP',
  'Laravel',
  'Qt',
];
</script>
