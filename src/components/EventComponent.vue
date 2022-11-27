<template>
  <button class="btn" @click="$emit('danceIn')">{{ statuSE }}</button>
  <button class="btn btn-error" @click="$emit('ranBowCheck')">
    {{ rainBow }}
  </button>
</template>

<script setup>
import { onMounted } from "vue";
const props = defineProps({
  statuSE: {
    type: String,
    default: "DEFAULT",
  },
  eRR: {
    type: String,
  },
  rainBow: {
    type: String,
    default: "no rainbow today",
  },
});
// defineProps({
//   statuSE: String,
// });
onMounted(() => {
  console.log(props.eRR);
});
defineEmits(["danceIn", "ranBowCheck"]);
</script>
