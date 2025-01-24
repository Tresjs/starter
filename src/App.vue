<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'

import TheExperience from './components/TheExperience.vue'
</script>

<template>
  <TresCanvas
    clear-color="#82DBC5"
    window-size
  >
    <TheExperience />
  </TresCanvas>
</template>
