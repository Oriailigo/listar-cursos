<template>
  <v-app>
    <v-main>
      <PxLista />
    </v-main>
  </v-app>
</template>

<script>
import PxLista from "@/components/PxLista";

export default {
  name: "App",

  components: {
    PxLista,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
#app {
  background-color: #121f3d;
}
</style>
