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
    <TresPerspectiveCamera :position="[7, 7, 7]" :look-at="[0, 4, 0]" />
    <TresScene>
      <TresGroup :position="[0, -4, 0]">
        <TresMesh :position="[-2, 6, 0]" :rotation="[0, Math.PI, 0]" cast-shadow>
          <TresConeGeometry :args="[1, 1.5, 3]" />
          <TresMeshToonMaterial color="#82DBC5" />
        </TresMesh>
        <TresMesh :position="[0, 4, 0]" cast-shadow>
          <TresBoxGeometry :args="[1.5, 1.5, 1.5]" />
          <TresMeshToonMaterial color="#4F4F4F" />
        </TresMesh>
        <TresMesh :position="[2, 2, 0]" cast-shadow>
          <TresSphereGeometry />
          <TresMeshToonMaterial color="#FBB03B" />
        </TresMesh>
      </TresGroup>

      <TresDirectionalLight :position="[0, 2, 4]" :intensity="0.75" cast-shadow />
    </TresScene>
  </TresCanvas>
</template>
