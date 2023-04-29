<script setup>
  import { ref, watch } from 'vue'
    
  const emit = defineEmits(['change-filter'])
  
  const checked = ref(null)
  
  watch(checked, (newChecked) => {
    emit('change-filter', newChecked)
  })
</script>

<template>
  <input type="radio" id="All" value="All" v-model="checked" checked>
  <label for = "All">All</label>
  
  <input type="radio" id="Open" value="Open" v-model="checked">
  <label for = "Open">Open</label>
  
  <input type="radio" id="Finished" value="Finished" v-model="checked">
  <label for = "Finished">Finished</label>  
</template>