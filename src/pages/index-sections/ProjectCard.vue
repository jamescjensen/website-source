<template>
  <v-card class="project-card" :elevation="2">
    <v-card-text>
      <div class="text-title-subsubsection">
        {{ project.title }}
      </div>

      <div class="content-stack">
        <div class="skill-list">
          <template v-for="skill in project.skills" :key="skill">
            <v-chip class="skill-chip" density="compact" size="small">{{ skill }}</v-chip>
          </template>
        </div>

        <div v-if="project.imageUrl">
          <v-img :alt="project.title" :src="project.imageUrl" />
        </div>

        <div>
          {{ project.description }}
        </div>

        <template v-for="link in project.externalLinks" :key="link.url">
          <div>
            <a :href="link.url">{{ link.text }}</a>
          </div>
        </template>
      </div>
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
  type ExternalLink = {
    text: string
    url: string
  }

  export type Project = {
    title: string
    description: string
    imageUrl?: string
    skills: string[]
    externalLinks?: ExternalLink[]
  }

  defineProps<{ project: Project }>()
</script>
