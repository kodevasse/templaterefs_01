<template>
  <div v-if="items" v-for="item in items">
    V-FOR: {{ item.name1 }} >>{{ item.age1 }} >>{{ item.groups1 }} >>
    {{ item.address1.city }}
  </div>
  CONST:
  <p>
    {{ name }} -- {{ AGE }} --
    <span v-for="group in groups"> {{ `${group} and ` }} </span>
  </p>
</template>

<script setup>
const props = defineProps({
  item: {
    type: Object,
    default: [],
  },
  items: {
    type: Object,
    default: "NO",
  },
});
const noob = "n00b";

const {
  name = "noNAME",
  age: AGE = `${noob}`,
  groups = "No groups",
} = props.item;
</script>
