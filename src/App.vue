<script setup>
import { markRaw } from 'vue'
import { VueFlow, useVueFlow } from '@vue-flow/core'
import { ref } from 'vue';
import myComp from './components/myComp.vue';
import myEdge from './components/myEdge.vue';
// import BraksComp from './components/BraksComp.vue';

const nodeTypes = {
  myCompNode: markRaw(myComp),
  // BraksCompNode: markRaw(BraksComp),
};

const edgeTypes = {
  myEdgeType: markRaw(myEdge)
};

const elements = ref([
  { id: 'node 1', type: 'myCompNode', active: true, position: { x: 50, y: 50 }},
  { id: 'node 2', type: 'myCompNode', active: false, position: { x: 200, y: 50 }},
  { id: 'node 3', type: 'myCompNode', active: false, position: { x: 50, y: 100 }},

  // { id: 'e1', source: 'node 1', target: 'node 2', sourceHandle: 's', targetHandle: 't' },
  { id: 'e1', type: 'myEdgeType', source: 'node 1', target: 'node 2', updatable: true}
])

const { onConnect, addEdges, onEdgeUpdate, updateEdge } = useVueFlow();
onConnect((params) => {
  addEdges([
    {
      ...params,
      type: 'myEdgeType',
      updatable: true
    }
  ])
})

onEdgeUpdate((params) => {
  updateEdge(params.edge, params.connection)
})

</script>

<!-- @connect="params => {params.type = 'myEdgeType'; addEdges(params)}" -->
<template>
  <div style="height: 900px; background: black">
    <VueFlow
      v-model="elements"
      :node-types="nodeTypes"
      :edge-types="edgeTypes"
    ></VueFlow>
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
