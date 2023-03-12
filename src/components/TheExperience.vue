<script setup lang="ts">
import { reactive } from 'vue'
import { BasicShadowMap, sRGBEncoding, NoToneMapping } from 'three'

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
    <OrbitControls />
    <TresPerspectiveCamera :position="[7, 7, 7]" :look-at="[0, 0, 0]" />
    <TresScene>
      <TresAmbientLight :intensity="0.5" />
      <TresMesh :position="[0, 2, 0]" cast-shadow>
        <TresSphereGeometry />
        <TresMeshToonMaterial color="#FBB03B" />
      </TresMesh>
      <TresDirectionalLight :position="[0, 2, 4]" :intensity="1" cast-shadow />
      <TresAxesHelper />
      <TresGridHelper :args="[10, 10, 0x444444, 'teal']" />
    </TresScene>
  </TresCanvas>
</template>
