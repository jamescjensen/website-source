<template>
  <expandable-area icon-size="20px">
    <template #title>
      <span class="text-title"> Introduction </span>
    </template>

    <div class="introduction-grid">
      <div>
        <p>
          Software engineer with 10 years of experience designing cloud-native
          applications and distributed backend systems. Experienced in system
          architecture, performance optimization, production infrastructure, and
          modernizing complex services across industrial SaaS, healthcare, and
          e-commerce industries. Specialized in Go, TypeScript/Node.js,
          Kubernetes, and AWS/GCP, with experience managing engineering teams.
        </p>

        <p>US citizen based in South Korea (F-2 visa; no sponsorship required).</p>

        <skill-sub-section />
      </div>

      <div class="portrait-container">
        <v-img
          alt="James (Jack) Jensen"
          :aspect-ratio="1"
          class="image"
          cover
          :src="portrait"
        />
      </div>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
  import portrait from '@/assets/me.jpeg'
  import ExpandableArea from '@/components/ExpandableArea.vue'
  import SkillSubSection from './SkillSubSection.vue'
</script>

<style scoped lang="scss">
.image {
  border-radius: 100px;
  flex-shrink: 0;
  max-height: 300px;
  max-width: 300px;
  width: 100%;
}
</style>
