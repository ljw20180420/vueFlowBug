<script setup>
import { computed } from 'vue'
import { BezierEdge, useEdge } from '@vue-flow/core'

const { edge } = useEdge()

edge.animated = computed(() => {
    const sourceNode = edge.sourceNode;
    return sourceNode.active;
})
</script>

<template>
    <BezierEdge/>
</template>