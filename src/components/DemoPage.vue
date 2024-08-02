<template>
  <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card" v-for="(item, i) in results" :key="i">
      <img :src="item.flags.png" height="150px" />
      <q-card-section>
        <div class="text-h6">Country Name: {{ item?.name?.common }}</div>
        <div class="text-subtitle2">Population: {{ item.population }}</div>
        <div class="text-subtitle2" text-no-wrap>
          Languages:
          <span v-for="lang of item.languages" :key="lang">
            {{ `${lang} ` }}
          </span>
        </div>
        <div class="text-subtitle2">
          Capital:
          <span v-for="(cap, j) in item.capital" :key="j">
            {{ `${cap} ` }}
          </span>
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script setup>
import axios from "axios";
import { onBeforeMount, ref } from "vue";

const results = ref("");

async function fetchCountry(params) {
  let endpoint = `https://restcountries.com/v3.1/region/${params}`;
  await axios
    .get(endpoint)
    .then((res) => {
      if (res.status === 200) {
        results.value = res.data;
      }
    })
    .catch((err) => {
      console.error(err.error);
    });
}

onBeforeMount(() => {
  fetchCountry("africa");
});
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
  height: 300px
</style>
