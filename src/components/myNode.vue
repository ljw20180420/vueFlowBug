<script setup>
import { useNode, Handle, Position, useHandleConnections, useVueFlow } from '@vue-flow/core';
const { node } = useNode();
const { addEdges } = useVueFlow();
const conns = useHandleConnections({
    type: 'source',
    id: 's',
    onConnect: params => {
        console.log("onConnect", params);
        // addEdges([
        //     {
        //         ...params,
        //         type: 'myEdgeType',
        //         updatable: true
        //     }
        // ])
    },
    onDisconnect: params => {
        console.log("onDisconnect", params);
    },
});
</script>

<template>
    <div>
        <span>{{ node.id }}</span>
        <Handle id="s" type="source" :position="Position.Right" />
        <Handle id="t" type="target" :position="Position.Left" />
        <input type="checkbox" v-model="node.active">
    </div>
</template>