<template>
  <v-dialog v-model="show"
            width="auto">
    <v-card>
      <slot></slot>
    </v-card>
  </v-dialog>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps([ 'show' ]);
const show = computed(() => props.show);
</script>

<style lang="scss" scoped>

</style>
