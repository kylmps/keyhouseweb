<template>
  <section class="bg">
    <div class="parent">
      <header class="header">
        <v-img
          :max-width="
            $vuetify.breakpoint.xs
              ? '120px'
              : $vuetify.breakpoint.sm
              ? '140px'
              : $vuetify.breakpoint.md
              ? '160px'
              : '180px'
          "
          :src="require('@/assets/keyhouse-logo.png')"
        ></v-img>
        <!-- <li class="nav">
          <ul>
            <h3>About</h3>
          </ul>
          <ul>
            <h3>Contact</h3>
          </ul>
        </li> -->
      </header>

      <!-- heading text -->
      <div class="heading-container">
        <h1 class="heading">Make your virtual event stand out.</h1>
      </div>

      <!-- button request a demo -->
      <div class="btn-container">
        <v-btn
          x-large
          depressed
          class="white--text btn"
          color="#f5b638"
          @click="showDiag = true"
        >
          Request a Demo
        </v-btn>
      </div>

      <!-- logo/portfolio transitioning -->

      <div class="logos mx-auto">
        <div
          class="d-flex item justify-center align-center"
          v-for="(image, i) in sponsors[currentSponsor].img"
          :style="{}"
          :key="i"
        >
          <v-img
            :key="cycle"
            :src="image"
            contain
            content-class="logo"
            max-width="100%"
            max-height="100%"
            min-width="100%"
            min-height="100%"
            :class="[
              cycle
                ? ` animate__animated animate__fadeIn`
                : 'animate__animated hide',
            ]"
            :style="{
              animationDelay: `${i}s`,
            }"
          ></v-img>
        </div>
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
import "animate.css";

export default {
  components: {
    DemoPopup: () => import("@/components/demo-popup.vue"),
  },
  data: () => ({
    currentSponsor: 0,
    cycle: true,
    time: 10000,
    sponsors: [
      {
        title: "First",
        img: [
          require("@/assets/one/one.png"),
          require("@/assets/one/two.png"),
          require("@/assets/one/three.png"),
          require("@/assets/one/four.png"),
          require("@/assets/one/five.png"),
          require("@/assets/one/six.png"),
          require("@/assets/one/seven.png"),
        ],
      },
      {
        title: "Second",
        img: [
          require("@/assets/two/one.png"),
          require("@/assets/two/two.png"),
          require("@/assets/two/three.png"),
          require("@/assets/two/four.png"),
          require("@/assets/two/five.png"),
          require("@/assets/two/six.png"),
          require("@/assets/two/seven.png"),
        ],
      },
    ],
  }),
  methods: {
    cycleSponsor() {
      this.time = this.currentSponsor == 0 ? 10000 : 10000;
      setTimeout(() => {
        this.cycle = false;
        setTimeout(() => {
          this.cycle = true;
        }, 100);
        if (this.currentSponsor < 2) {
          this.currentSponsor++;
        } else {
          this.currentSponsor = 0;
        }
        this.cycleSponsor();
      }, this.time);
    },
  },
  mounted() {
    this.cycleSponsor();
  },
};
</script>

<style lang="scss" scoped>
.bg {
  height: 100%;
  background-color: #7776bc;
}

.parent {
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
  margin: 0 1.6rem;
  margin-top: 1.2rem;
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

.hide {
  opacity: 0;
}
.logos {
  width: 60%;
  height: 100%;
  max-width: 65%;
  display: flex;
  justify-content: center;
  align-items: center;
  // flex-wrap: wrap;
}
.logo {
  min-width: 80px;
}
.b {
  max-width: 1000px;
}
.sponsors {
  width: 100%;
  height: 130px;
  font-size: 1.3rem;
  z-index: 30;
}
.item {
  min-width: 9%;
  max-width: 19%;
  max-height: 46px;
  min-height: 45px;
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
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  li {
    // border: #fffbdb 2px solid;
    // width: 10rem;
    margin: auto 1.2rem;
  }
}

.footer-container {
  flex: 1;
  margin-top: 1.2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer {
  color: #fffbdb;
  font-weight: 10;
  font-size: 1.2rem;
  padding-bottom: 1.6rem;
}

@media (max-width: 1200px) {
  .parent {
    // overflow: hidden;
    gap: 4.8rem;
  }
  .heading {
    font-size: 3.2rem;
  }
}

@media (max-width: 600px) {
  .logos {
    width: 70%;
    display: flex;
    flex-wrap: wrap;
    height: 10px;
  }
  .logo {
    max-width: 50px !important;
    max-height: 30px;
  }
  .item {
    min-width: 10%;
    max-width: 12%;
    max-height: 30px;
    min-height: 30px;
  }
  .parent {
    // overflow: hidden;
    gap: 4.2rem;
  }
  .heading {
    font-size: 2.4rem;
  }

  .footer {
    font-size: 0.8rem;
    padding-bottom: 0.8rem;
  }

  .header {
    margin-bottom: 1.2rem;
  }

  .nav {
    font-size: 1rem;
  }
}
</style>
