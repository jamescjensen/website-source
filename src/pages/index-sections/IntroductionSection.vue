<template>
  <expandable-area icon-size="20px">
    <template #title>
      <span class="text-title"> Introduction </span>
    </template>
    <div class="row q-col-gutter-sm items-center justify-between">
      <div class="col-xs-12 col-sm-9">
        Developer with ten years of professional experience building
        cloud-native applications, distributed systems, and e-commerce
        platforms; delivering high-scale services on AWS and GCP. Experienced
        leading cross-functional teams through architecture design, roadmap
        planning, and delivery. Specialized in Go, Node.js, and cloud
        infrastructure.
        <skill-sub-section />
      </div>

      <div class="col-xs-12 col-sm-3 row justify-center">
        <q-img class="image" fit="cover" no-spinner src="~assets/me.jpeg" />
      </div>
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import SkillSubSection from './SkillSubSection.vue';
import ExpandableArea from 'components/ExpandableArea.vue';
</script>

<style scoped lang="scss">
.image {
  border-radius: 100px;
  flex-shrink: 0;
  max-height: 300px;
  max-width: 300px;
}
</style>
