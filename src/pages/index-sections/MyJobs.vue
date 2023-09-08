<template>
  <expandable-area icon-size="20px">
    <template #title> <span class="text-title">My Jobs</span></template>
    <div class="row q-col-gutter-sm">
      <template v-for="job in jobs" :key="job.company">
        <expandable-area class="col-12" icon-size="18px">
          <template #title>
            <span class="text-title-subsection q-pr-sm">
              {{ job.company }}
            </span>

            <span class="text-subtitle-subsection q-pr-sm">
              {{ job.title }}
            </span>

            <span
              class="text-subtitle-subsection"
              :style="{ fontStyle: 'italic' }"
            >
              {{ job.dateRange }}
            </span>
          </template>
          <div class="row q-col-gutter-sm">
            <div class="col-12">
              {{ job.description }}
            </div>
            <template v-for="skill in job.skills" :key="skill">
              <div class="col-auto">
                <q-chip class="skill-chip" dense :label="skill" />
              </div>
            </template>

            <div class="col-12">Projects</div>

            <div class="col-12 row q-col-gutter-md q-px-md">
              <template v-for="project in job.projects" :key="project.title">
                <expandable-area class="col-12" icon-size="14px">
                  <template #title>
                    <span class="text-title-subsubsection">
                      {{ project.title }}
                    </span>
                  </template>
                  <div class="row q-col-gutter-sm">
                    <template v-if="project.imageUrl">
                      <div class="col-4">
                        <q-img :src="project.imageUrl" />
                      </div>
                      <div class="col-8">
                        {{ project.description }}
                      </div>
                    </template>
                    <template v-else>
                      <div class="col-12">
                        {{ project.description }}
                      </div>
                    </template>
                    <template v-for="skill in project.skills" :key="skill">
                      <div class="col-auto">
                        <q-chip class="skill-chip" dense :label="skill" />
                      </div>
                    </template>
                  </div>
                </expandable-area>
              </template>
            </div>
          </div>
        </expandable-area>
      </template>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import { faker } from '@faker-js/faker';

import ExpandableArea from 'components/ExpandableArea.vue';

type Project = {
  title: string;
  description: string;
  imageUrl?: string;
  skills: string[];
};

type Job = {
  company: string;
  description: string;
  title: string;
  dateRange: string;
  imageUrl?: string;
  skills: string[];
  projects: Project[];
};

const jobs: Job[] = [];

for (let i = 0; i < 5; i++) {
  const newJob: Job = {
    company: 'Company ' + i,
    title: 'Job Title ' + i,
    dateRange: 'Aug 1994 - Aug 1995',
    description: faker.lorem.paragraphs(),
    skills: [
      'JavaScript',
      'TypeScript',
      'Node.js',
      'Vue',
      'Quasar',
      'Flutter / Dart',
      'Google Cloud',
      'PHP',
      'Laravel',
    ],
    projects: [],
  };

  for (let i = 0; i < 3; i++) {
    newJob.projects.push({
      title: 'Project ' + i,
      description: faker.lorem.paragraphs(),
      skills: [
        'JavaScript',
        'TypeScript',
        'Node.js',
        'Vue',
        'Quasar',
        'Flutter / Dart',
        'Google Cloud',
        'PHP',
        'Laravel',
      ],
      imageUrl: Math.random() > 0.75 ? faker.image.url() : undefined,
    });
  }
  jobs.push(newJob);
}
</script>
