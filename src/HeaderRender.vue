<script setup lang="ts">

import type {Ref} from "vue";
import {getCurrentInstance, ref} from "vue";

const instance = getCurrentInstance();
const filterIcon: Ref<HTMLDivElement | null> = ref(null);

const filter=()=>{
  (instance!.data.params! as any).showColumnMenu(filterIcon.value!);
}
</script>

<template>
<div ref="filterIcon">表头 <button @click="filter">filter</button></div>
</template>

<style scoped>

</style>
