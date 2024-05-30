<script setup>
import { markRaw } from 'vue'
import { VueFlow, useVueFlow } from '@vue-flow/core'
import { ref } from 'vue';
import myComp from './components/myComp.vue';

const nodeTypes = {
  myCompNode: markRaw(myComp),
};

const { addEdges } = useVueFlow();

const elements = ref([
  { id: 'node 1', type: 'myCompNode', position: { x: 50, y: 50 }},
  { id: 'node 2', type: 'myCompNode', position: { x: 200, y: 50 }},

  { id: 'e1', source: 'node 1', target: 'node 2' },
])

function onConnect(params) {
  addEdges(params);
  console.log("onConnect", params);
}
</script>

<template>
  <div style="height: 900px; background: black">
    <VueFlow
      v-model="elements"
      :node-types="nodeTypes"
    >
    </VueFlow>
  </div>
</template>

<style>
/* import the necessary styles for Vue Flow to work */
@import '@vue-flow/core/dist/style.css';

/* import the default theme, this is optional but generally recommended */
@import '@vue-flow/core/dist/theme-default.css';

.vue-flow__node {
    background: green;
    color: white;
    border: 0px solid black;
    border-radius: 4px;
    box-shadow: 0 0 0 4px blue;
    padding: 0px;
}
</style>
