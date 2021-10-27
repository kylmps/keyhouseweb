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
      <!-- batch one -->
      <ul class="client-logo-container">
        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="one" key="a" :src="require('@/assets/one/one.png')"></v-img>
            <v-img v-if="!one" key="b" :src="require('@/assets/two/one.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="two" key="a" :src="require('@/assets/one/two.png')"></v-img>
            <v-img v-if="!two" key="b" :src="require('@/assets/two/two.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="three" :src=" require('@/assets/one/three.png')"></v-img>
            <v-img v-if="!three" key="b" :src="require('@/assets/two/three.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="four" key="a" :src="require('@/assets/one/four.png')"></v-img>
            <v-img v-if="!four" key="b" :src="require('@/assets/two/four.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="five" key="a" :src="require('@/assets/one/five.png')"></v-img>
            <v-img v-if="!five" key="b" :src="require('@/assets/two/five.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="six" key="a" :src="require('@/assets/one/six.png')"></v-img>
            <v-img v-if="!six" key="b" :src="require('@/assets/two/six.png')"></v-img>
          </transition>
        </li>

        <li>
          <transition name="slide" mode="out-in">
            <v-img v-if="seven" key="a" :src="require('@/assets/one/seven.png')"></v-img>
            <v-img v-if="!seven" key="b" :src="require('@/assets/two/seven.png')"></v-img>
          </transition>
        </li>
      </ul>

      <!-- batch two -->
      <!-- <ul class="client-logo-container">
        <li>
          <v-img
            class="twotwo"
            max-width="100vw"
            :src="require('@/assets/two/one.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/two.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/three.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/four.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/five.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/six.png')"
          ></v-img>
        </li>
        <li>
          <v-img
            class="two"
            max-width="100vw"
            :src="require('@/assets/two/seven.png')"
          ></v-img>
        </li>
      </ul> -->

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
    one: true,
    two: true,
    three: true,
    four: true,
    five: true,
    six: true,
    seven: true,
  }),
  mounted() {
    setInterval(() => {
      this.one = !this.one;
      this.two = !this.two;
      this.three = !this.three;
      this.four = !this.four;
      this.five = !this.five;
      this.six = !this.six;
      this.seven = !this.seven;
    }, 10000);
    // setInterval(() => {
    //   this.two = !this.two;
    // }, 13000);
    // setInterval(() => {
    //   this.three = !this.three;
    // }, 15000);
    // setInterval(() => {
    //   this.four = !this.four;
    // }, 9000);
    // setInterval(() => {
    //   this.five = !this.five;
    // }, 18000);
    // setInterval(() => {
    //   this.six = !this.six;
    // }, 8000);
    // setInterval(() => {
    //   this.seven = !this.seven;
    // }, 17000);
  },
};
</script>

<style lang="scss" scoped>
slide-enter-active,
.slide-leave-active {
  transition: all 0.8s;
}
.slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(+100%);
}
.slide-enter {
  opacity: 1;
  transform: translateY(-100%);
}

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
