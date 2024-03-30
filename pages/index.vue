<template>
  <div :class="`container ${isShow ? 'border' : ''}` ">
    <VueDraggable
      v-model="list2"
      :animation="200"
      @add="add"
      group="people">
        <div class="py-5">

        </div>
      <div
        v-for="(item,index) in list2"
        :key="item.id"
        class="border d-flex align-items-center shadow bg-light mb-4 p-3"
      >
        {{ item.name }}
        <button @click="list2.splice(index,1)" class="btn-close ms-auto"></button>
      </div>
    </VueDraggable>
  </div>
</template>

<script lang="ts" setup>
import { VueDraggable } from 'vue-draggable-plus'

const list2 = inject('list2')

const isShow = computed(()=>list2.value == undefined || list2.value.length == 0)
const add = (e)=>{
  list2.value = list2.value.map(item => ({
    name: `${item.name}`,
    id: generateUUID()
  }))
}
</script>

<style>

</style>