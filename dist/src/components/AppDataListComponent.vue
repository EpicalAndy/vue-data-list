<template>
  <v-table>
    <thead>
    <tr>
      <th>Name</th>
      <th>Value</th>
      <th>Actions</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="item in dataList" :key="item.id">
      <td>{{ item.name }}</td>
      <td>{{ item.value }}</td>
      <td>
        <app-button-component @click="startEdit(item)">
          <v-icon>mdi-pencil</v-icon>
        </app-button-component>
      </td>
    </tr>
    </tbody>
  </v-table>

  <app-form-component v-if="editedCard"
                      :card="editedCard"
                      @update-card="updateCard">
  </app-form-component>
</template>

<script setup>
import { data } from "@/demo/data";
import AppButtonComponent from "@/components/AppButtonComponent.vue";
import { ref } from "vue";
import AppFormComponent from "@/components/AppFormComponent.vue";

const dataList = ref(data.map((item, index) => {
  item.id = index;

  return item;
}));
const editedCard = ref(null);

function startEdit(item) {
  editedCard.value = item;
}

function updateCard(card) {
  const currentCard = dataList.value.find(item => item.id === card.id);

  currentCard && (currentCard.value = card.value, editedCard.value = null);
}
</script>

<style lang="scss" scoped>

</style>
