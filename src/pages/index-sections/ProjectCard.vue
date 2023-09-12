<template>
  <q-card>
    <q-card-section>
      <div class="text-title-subsubsection">
        {{ project.title }}
      </div>
      <div class="row q-col-gutter-sm">
        <template v-for="skill in project.skills" :key="skill">
          <div class="col-auto">
            <q-chip class="skill-chip" dense :label="skill" />
          </div>
        </template>
        <div v-if="project.imageUrl" class="col-12">
          <q-img :src="project.imageUrl" />
        </div>
        <div class="col-12">
          {{ project.description }}
        </div>

        <template v-for="link in project.externalLinks" :key="link.url">
          <div class="col-auto">
            <a :href="link.url">{{ link.text }}</a>
          </div>
        </template>
      </div>
    </q-card-section>
  </q-card>
</template>

<script setup lang="ts">
type ExternalLink = {
  text: string;
  url: string;
};

export type Project = {
  title: string;
  description: string;
  imageUrl?: string;
  skills: string[];
  externalLinks?: ExternalLink[];
};

defineProps<{ project: Project }>();
</script>
