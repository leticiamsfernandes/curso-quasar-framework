<template>
  <q-page class="flex flex-center">
    <q-tabs v-model="tab" class="text-teal">
      <q-tab name="mails" icon="mail" label="Mails" />
      <q-tab name="alarms" icon="alarm" label="Alarms" />
      <q-tab name="movies" icon="movie" label="Movies" />
    </q-tabs>
  </q-page>
</template>

<style>
</style>

<script>
import { ref } from "vue";

export default {
  name: "HelloWorld",
  setup() {
    return {
      tab: ref("mails"),
    };
  },
};
</script>
