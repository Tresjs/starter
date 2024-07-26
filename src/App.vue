<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'

import TheExperience from './components/TheExperience.vue'
import MyButton from './components/MyButton.vue'
</script>

<template>
  <MyButton />
  <TresCanvas clear-color="#82DBC5" window-size>
    <TheExperience />
  </TresCanvas>
</template>
