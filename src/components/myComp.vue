<script setup>
import { Handle, useHandleConnections, Position } from '@vue-flow/core';
const connections = useHandleConnections({
    type: "source",
    onConnect: (params) => {
        console.log("onConnect", params);
    },
    onDisConnect: (params) => {
        console.log("onDisConnect", params);
    },
});
</script>

<template>
    <div>
        <span>A node</span>
        <Handle type="source" :position="Position.Right" />
        <Handle type="target" :position="Position.Left" />
    </div>
</template>