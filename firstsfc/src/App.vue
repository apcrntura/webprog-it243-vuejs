<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'
 
const instruments = ref([])
 
async function getInstruments() {
  const { data } = await supabase.from('instruments').select()
  instruments.value = data
}
 
onMounted(() => {
   getInstruments()
})
</script>
 
<template>
  <ul>
    <li v-for="instrument in instruments" :key="instrument.id">{{ instruments.name }}</li>
  </ul>
</template>