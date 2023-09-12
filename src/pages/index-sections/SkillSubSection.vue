<template>
  <expandable-area icon-size="18px">
    <template #title>
      <span class="text-title-subsection"> Skills </span>
    </template>
    <div class="row q-col-gutter-sm">
      <div class="col-12">
        <div class="text-title-subsubsection">
          {{ '>=5 Years' }}
        </div>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in fiveYearSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </div>
      <div class="col-12">
        <div class="text-title-subsubsection">
          {{ '2~5 Years' }}
        </div>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in twoYearSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </div>
      <div class="col-12">
        <div class="text-title-subsubsection">{{ '<2 Years' }}</div>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in someExperienceSkills" :key="skill">
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

const fiveYearSkills = [
  'JavaScript',
  'TypeScript',
  'Node.js',
  'AWS',
  'HTML',
  'CSS',
];

const twoYearSkills = ['Google Cloud', 'Quasar', 'Vue', 'React', 'Perl'];

const someExperienceSkills = [
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
