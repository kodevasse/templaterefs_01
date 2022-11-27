<script setup>
import { useLocalStorage, useMouse, usePreferredDark } from "@vueuse/core";
import EventComponentVue from "../components/EventComponent.vue";
import { ref, onMounted, computed } from "vue";
// tracks mouse position
const { x, y } = useMouse();

// is user prefers dark theme
const isDark = usePreferredDark();

// persist state in localStorage
const store = useLocalStorage("my-storage", {
  name: "Apple",
  color: "red",
});
const calcThis = () => {
  console.log("EVENT FROM EventComponentVue");
  state.value = !state.value;
};
const rainBowActivate = () => {
  if (rainBow.value === "heavy") {
    rainBow.value = "light";
  } else {
    rainBow.value = "heavy";
  }
};

const state = ref(false);
const e = computed(() => {
  return state.value ? "fisk" : "duck";
});

const er = computed(() => {
  if (e.value === "fisk") return "E IS FISK";
  return "E IS NOT FISK";
});
const rainBow = ref("heavy");

const erNOT = computed(() => {
  if (e.value === "fisk") return "";
  return "NOT";
});
</script>

<template>
  <main>
    <EventComponentVue
      :statuSE="e"
      :eRR="er"
      :rainBow="rainBow"
      @dance-In="calcThis"
      @ranBowCheck="rainBowActivate"
    />
    /// {{ e }} /// is
    <span class="text-red-300">{{ erNOT }}</span>
    fisk
  </main>
</template>
