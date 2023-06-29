<template>
  <v-row>
    <v-col cols="4">
      <app-dialog-component :show="card !== null">
        <v-card>
          <v-card-title>Edit card</v-card-title>
          <v-responsive
            class="mx-auto"
            min-width="344"
          >
            <v-card-item>
               <v-label>Name</v-label>
              <v-text-field :disabled="true"
                            v-model="cardName"
              >
              </v-text-field>
            </v-card-item>

            <v-card-item>
              <v-label>Value</v-label>
              <v-text-field v-model="cardValue"></v-text-field>
            </v-card-item>
          </v-responsive>

          <app-button-component @click="updateCard">ОК</app-button-component>
        </v-card>
      </app-dialog-component>
    </v-col>
  </v-row>
</template>

<script setup>
import AppDialogComponent from "@/components/AppDialogComponent.vue";
import { computed, ref } from "vue";
import AppButtonComponent from "@/components/AppButtonComponent.vue";

const props = defineProps([ 'card' ]);
const card = Object.assign({}, props.card);
const cardValue = ref(card.value);
const cardName = computed(() => card.name);
const emits = defineEmits(['updateCard'])
function updateCard() {
  card.value = cardValue.value;
  emits("updateCard", card);
}
</script>

<style lang="scss" scoped>

</style>
