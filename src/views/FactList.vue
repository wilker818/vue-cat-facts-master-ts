<template>
  <div class="list-group">
    <a
      class="list-group-item list-group-item-action clickable"
      v-for="(fact, i) in facts"
      :key="i"
      @click="goToFact(i)"
    >
      <div class="row">
        <div class="col-2"><img :src="fact.image" height="40" /></div>
        <div class="col-10 align-self-center">{{ fact.text }}</div>
      </div>
    </a>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRouter } from "vue-router";

import { facts } from "@/assets/facts";
export default defineComponent({
  name: "cat-fact-list",
  setup() {
    const router = useRouter();
    const goToFact = (id: number) => {
      router.push({ path: `/fact/${id}` });
    };
    return { facts, goToFact };
  },
});
</script>

<style scoped>
.clickable {
  cursor: pointer;
}
</style>
