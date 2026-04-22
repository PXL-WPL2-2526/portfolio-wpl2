<script setup>
import { useRoute } from 'vue-router'
import { computed } from 'vue'
import projects from '@/projects/projects.json'
import ProjectPage from '@/views/ProjectPage.vue'

const route = useRoute()

const currentIndex = computed(() =>
    projects.findIndex(p => p.id === route.params.id)
)

const project = computed(() =>
    currentIndex.value !== -1 ? projects[currentIndex.value] : null
)

const prevProject = computed(() =>
    projects[(currentIndex.value - 1 + projects.length) % projects.length]
)

const nextProject = computed(() =>
    projects[(currentIndex.value + 1) % projects.length]
)
</script>

<template>
  <ProjectPage
      v-if="project"
      :project="project"
      :prev="prevProject"
      :next="nextProject"
  />

  <div v-else>Project not found</div>
</template>