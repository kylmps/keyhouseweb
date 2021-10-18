<template>
  <v-app>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  // 
  // background-color: #7776bc;
  font-size: 62.5%;
}

@font-face {
  font-family: Avenir;
  font-style: normal;
  font-weight: 200;
  src: url('./assets/font/Avenir.ttf') format('TrueType');
}

#app {
  font-family: Avenir, "Sans Serif";
}
</style>
