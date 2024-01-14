<script setup lang="ts">

import {PropType} from "vue";

type Field = {
  label: string,
  key: string | number,
}

const props = defineProps({
  fields: {
    type: Array as PropType<Field[]>,
    default: [],
  },
  data: {
    type: Array as PropType<any[]>,
    default: [],
  }
})

const emits = defineEmits(['rowClick'])

</script>

<template>
  <div class="table-container">
    <table class="table">
      <thead>
      <tr>
        <th v-for="field in fields">{{ field.label }}</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="row in data" @click="$emit('rowClick', row)"
          class="hover">
        <td v-for="field in fields">{{ row[field.key] }}</td>
      </tr>
      </tbody>
      <tfoot>
      <tr>
        <th v-for="field in fields">{{ field.label }}</th>
      </tr>
      </tfoot>
    </table>
  </div>
</template>

<style scoped>
.table {
}
</style>