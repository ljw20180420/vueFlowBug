<script setup>
import { useNode, Handle, Position, useHandleConnections, useVueFlow } from '@vue-flow/core';
const { node } = useNode();
const { addEdges } = useVueFlow();
const conns = useHandleConnections({
    type: 'source',
    // id: 's',
    onConnect: (params) => {
        console.log("onConnect", params);
    },
    onDisconnect: (params) => {
        console.log("onDisconnect", params);
    },
});
</script>

<template>
    <div>
        <span>{{ node.id }}</span>
        <Handle type="source" :position="Position.Right" />
        <Handle type="target" :position="Position.Left" />
        <input type="checkbox" v-model="node.active">
    </div>
</template>