<template>
  <button class="btn" @click="$emit('danceIn')">{{ statuSE }}</button>
  <button
    class="p-2 w-16 rounded-full"
    :class="rainBowColor"
    @click="$emit('ranBowCheck')"
  >
    {{ rainBow }}
  </button>
</template>

<script setup>
import { onMounted, computed } from "vue";

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

const rainBowColor = computed(() => {
  if (props.rainBow === "heavy") return "bg-red-400 text-black";
  else if (props.rainBow === "light")
    return "bg-blue-300 text-black  bg-opacity-70";
  else return "bg-gray-800";
});

onMounted(() => {
  console.log(props.eRR);
});
defineEmits(["danceIn", "ranBowCheck"]);

// set timeout function
setTimeout(() => {
  console.log("Delayed for 1 second.");
}, "1000");
</script>
