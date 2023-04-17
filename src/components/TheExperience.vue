<script setup lang="ts">
import { TresCanvas } from '@tresjs/core'
import { reactive } from 'vue'
import { BasicShadowMap, sRGBEncoding, NoToneMapping } from 'three'
import TheModel from './TheModel.vue'
import { OrbitControls } from '@tresjs/cientos'

const state = reactive({
  clearColor: '#82DBC5',
  shadows: true,
  alpha: false,
  shadowMapType: BasicShadowMap,
  outputEncoding: sRGBEncoding,
  toneMapping: NoToneMapping,
})
</script>

<template>
  <TresCanvas v-bind="state">
    <TresPerspectiveCamera :position="[7, 7, 7]" :look-at="[0, 0, 0]" />
    <OrbitControls />
    <TresAmbientLight :intensity="0.5" :color="'red'" />
    <Suspense>
      <TheModel />
    </Suspense>
    <TresDirectionalLight :position="[0, 2, 4]" :intensity="1" cast-shadow />
    <TresAxesHelper />
    <TresGridHelper :args="[10, 10, 0x444444, 'teal']" />
  </TresCanvas>
</template>
