<script setup>
import { useNode, Handle, Position, useHandleConnections, useVueFlow } from '@vue-flow/core';
const { node } = useNode();
const { addEdges } = useVueFlow();
useHandleConnections({
    type: 'source',
    id: 'source',
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
        <Handle id="source" type="source" :position="Position.Right" />
        <Handle id="target" type="target" :position="Position.Left" />
    </div>
</template>