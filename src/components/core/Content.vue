<template>
  <v-main class="bg">
      <v-fab-transition >
          <router-view />
      </v-fab-transition>
  </v-main>
</template>

<script>
export default {

}
</script>

<style scoped>
.bg{
    background-color: darkslategray;
    height: 100%;
}
</style>