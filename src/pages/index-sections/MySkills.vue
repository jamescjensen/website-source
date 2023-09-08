<template>
  <expandable-area icon-size="20px">
    <template #title>
      <span class="text-title"> My Skills </span>
    </template>
    <div class="row q-col-gutter-sm">
      <expandable-area class="col-12" icon-size="18px">
        <template #title>
          <span class="text-title-subsection">
            {{ '>=5 Years' }}
          </span>
        </template>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in fiveYearSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </expandable-area>
      <expandable-area class="col-12" icon-size="18px">
        <template #title>
          <span class="text-title-subsection">
            {{ '2~5 Years' }}
          </span>
        </template>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in twoYearSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </expandable-area>
      <expandable-area class="col-12" icon-size="18px">
        <template #title>
          <span class="text-title-subsection"> {{ '<2 Years' }} </span>
        </template>
        <div class="row q-col-gutter-sm">
          <template v-for="skill in someExperienceSkills" :key="skill">
            <div class="col-auto">
              <q-chip class="skill-chip" dense :label="skill" />
            </div>
          </template>
        </div>
      </expandable-area>
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
];
</script>
