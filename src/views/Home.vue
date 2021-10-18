<template>
  <section class="bg">
    <div class="parent">
      <header class="header mx-15 pt-5">
        <v-img
          max-width="200px"
          :src="require('@/assets/keyhouse-logo.png')"
        ></v-img>
        <li class="nav">
          <ul>
            <h3>About</h3>
          </ul>
          <ul>
            <h3>Contact</h3>
          </ul>
        </li>
      </header>

      <!-- heading text -->
      <div class="heading-container">
        <h1 class="heading">Make your virtual event stand out.</h1>
      </div>

      <!-- button request a demo -->
      <div class="btn-container">
        <v-btn depressed class="white--text btn" color="#f5b638" @click="showDiag = true">
          Request a Demo
        </v-btn>
      </div>

      <!-- logo/portfolio transitioning -->
      <div class="client-logo-container">
        <v-img
          class="top"
          max-width="88vw"
          :src="require('@/assets/top.png')"
        ></v-img>
      </div>

      

      <DemoPopup :show="showDiag" @close="showDiag = false"></DemoPopup>
    
    <!-- footer -->
    <footer class="footer-container">
        <h4 class="footer">Manila, Philippines</h4>
      </footer>

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
  height: 100%;
  background-color: #7776bc;
  // overflow: overlay !important;
  // overflow-x: hidden !important;
}

.parent {
  // overflow: hidden;
  padding: 0 0;
  display: flex;
  gap: 5.2rem;
  flex-direction: column;
}

.heading-container {
  display: flex;
  align-items: center;
  justify-content: center;
}

.header {
  margin-bottom: 3.2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .nav {
    list-style: none;
    display: flex;
  }
  li h3 {
    display: block;
    color: white;
    text-align: center;
    text-decoration: none;
  }
}

.logo {
  order: 1;
}
.about {
  order: 2;
}
.contact {
  order: 3;
}

.heading {
  text-align: center;
  font-size: 4rem;
  color: #fffbdb;
  font-weight: 5;
  letter-spacing: 3px;
  padding: 3.2rem 3.2rem;
}

.btn-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 3.2rem;
}

.btn {
  text-transform: none;
}

.client-logo-container {
  // display: flex;
  // align-items: center;
  // justify-content: center;
  // margin-bottom: 4%;
}

.top {
  margin: auto;
}

.footer-container {
  flex: 1;
  margin-top: 2.4rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer {
  // margin-top: 3%;
  color: #fffbdb;
  font-weight: 10;
  font-size: 1rem;
  padding-bottom: 1.6rem;
}
</style>
