<script setup>
import { useLocalStorage, useMouse, usePreferredDark } from "@vueuse/core";
import EventComponentVue from "../components/EventComponent.vue";
import ListComponent from "@/components/ListComponent.vue";
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

const item = {
  name: "trond",
  age: 32,
  groups: ["fishing", "astronomy"],
  address: { city: "Somewhere", country: "Norway" },
};
const items = [
  {
    name1: "LEIF",
    age1: 12,
    groups1: ["fishing", "astronomy"],
    address1: { city: "Somewhere1", country: "Norway1" },
  },
  {
    name1: "Veigar",
    age1: 92,
    groups1: ["fotball", "computer science"],
    address1: { city: "Somewhere2", country: "Norway2" },
  },
];
</script>

<template>
  <main>
    <div class="flex flex-col w-full">
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

      <ListComponent :item="item" :items="items" />
    </div>
  </main>
</template>
