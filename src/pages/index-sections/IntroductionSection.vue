<template>
  <expandable-area icon-size="20px">
    <template #title>
      <span class="text-title"> Introduction </span>
    </template>
    <div class="row q-col-gutter-sm justify-between">
      <div class="col-9">
        My name is James Jensen (nickname Jack) and I am a software engineer
        with 7 years of professional experience, living in Seoul, South Korea.
        I've done front-end engineering, back-end engineering, embedded
        engineering, server architecture.. and I'm always happy to try more. I'm
        most familiar with Node.js, but every job I've had has involved learning
        a new programming language on the spot, and again, always happy to try
        more.

        <skill-sub-section />
      </div>

      <q-img
        class="col-3 image-container"
        fit="cover"
        no-spinner
        src="~assets/me.jpeg"
      />
    </div>
  </expandable-area>
</template>

<script setup lang="ts">
import SkillSubSection from './SkillSubSection.vue';
import ExpandableArea from 'components/ExpandableArea.vue';
</script>

<style scoped lang="scss">
.image-container {
  border-radius: 100px;
  flex-shrink: 0;
  max-height: 300px;
  max-width: 300px;
}
</style>
