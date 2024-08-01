<template>
  <q-page class="flex flex-center">
    <div style="display: grid;">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
    <q-btn style="margin: 20px;" to="/demo"> Go To Demo Page </q-btn>
    </div>
  </q-page>
</template>

<script setup>
defineOptions({
  name: 'IndexPage'
});
</script>
