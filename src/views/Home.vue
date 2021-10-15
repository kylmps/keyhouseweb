<template>
  <section class="bg">
    <div class="parent">
      <div class="header-container">
        <!-- header logo -->
        <div class="logo">
          <v-img
            max-width="3%"
            :src="require('@/assets/keyhouse-logo.png')"
          ></v-img>
        </div>
        <div class="about">
          <h3>About</h3>
        </div>
        <div class="contact">
          <h3>Contact</h3>
        </div>
      </div>

      <!-- heading text -->
      <div class="heading-container">
        <h1 class="heading">Make your virtual event stand out.</h1>
      </div>

      <!-- button request a demo -->
      <div class="btn-container">
        <v-btn class="white--text btn" color="#f5b638" @click="showDiag = true">
          Request a Demo
        </v-btn>
      </div>

      <!-- logo/portfolio transitioning -->
      <div class="client-logo-container">
        <v-img
          class="top"
          max-width="85%"
          :src="require('@/assets/top.png')"
        ></v-img>
        <!-- <v-img></v-img> -->
      </div>

      <!-- footer -->
      <div class="footer-container">
        <h4 class="footer">Manila, Philippines</h4>
      </div>

      <DemoPopup :show="showDiag" @close="showDiag = false"></DemoPopup>
    </div>
  </section>
</template>

<script>
export default {
  components: {
    DemoPopup: () => import("@/components/demo-popup.vue"),
  },
  data: () => ({
    showDiag: false,
  }),
};
</script>

<style lang="scss" scoped>
.bg {
  background-color: #7776bc;
  padding: 0 0;
}

.parent {
  max-width: 130rem;
  margin: 0 auto;
}

.heading-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 4%;
}


.header-container {
  display: flex;
}

.logo {
  order: 1;
  justify-self: flex-start;
  margin-top: 3rem;
  margin-left: 5%;
  margin-bottom: 14%;
  // padding: 1.2rem 7rem;
}

.about {
  order: 2;
  background: red;
}

.contact {
  order: 3;
}

.heading {
  font-size: 4rem;
  color: #fffbdb;
  font-weight: 5;
  letter-spacing: 3px;
}

.btn-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 8%;
}

.client-logo-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 4%;
}

.footer-container {
  // margin-top: 25.8rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.6%;
}

.footer {
  color: #fffbdb;
  font-weight: 10;
  font-size: 1rem;
}
</style>
