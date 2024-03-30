<template>
    <VueDraggable
      v-model="list1"
      :animation="150"
      :group="{ name: 'people', pull: 'clone', put: false }"
      :sort="false"
      class="flex flex-col gap-2 p-4 w-300px bg-gray-500/5 rounded" 
    >
      <div
        v-for="item in list1"
        :key="item.id"
        class="cursor-move h-50px bg-gray-500/5 rounded p-3"
      >
        {{ item.name }}
      </div>
    </VueDraggable>
  <div>
    <slot />
  </div>
</template>

<script lang="ts" setup>
import { VueDraggable } from 'vue-draggable-plus'
const list1 = inject('list1')
</script>

<style>

</style>