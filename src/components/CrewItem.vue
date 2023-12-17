<template>
  <main>
    <section class="section-two">
      <div :class="{ fadeIn: animate }">
        <h4>{{ this.items[this.i].role }}</h4>
        <h3>{{ this.items[this.i].name }}</h3>
        <p class="dest-info">
          {{ this.items[this.i].bio }}
        </p>
        <nav>
        <span
          v-on:click="
            i = 0;
            handleNavClick();
            items[0].isActive = true;
          "
          :class="{ active: this.items[0].isActive }"
          >Douglas</span
        >
        <span
          v-on:click="
            i = 1;
            handleNavClick();
            items[1].isActive = true;
          "
          :class="{ active: this.items[1].isActive }"
          >Mark</span
        >
        <span
          v-on:click="
            i = 2;
            handleNavClick();
            items[2].isActive = true;
          "
          :class="{ active: this.items[2].isActive }"
          >Victor</span
        >
        <span
          v-on:click="
            i = 3;
            handleNavClick();
            items[3].isActive = true;
          "
          :class="{ active: this.items[3].isActive }"
          >Anousheh</span
        >
      </nav>
      </div>
    </section>
    <section class="section-one">
      <img
        class="dest-img" :class="{ fadeIn: animate }"
        :src="require('../assets/crew/' + this.items[this.i].images.webp)"
        width="500"
      />
    </section>
  </main>
</template>

<script>
import data from '../assets/data.json';

export default {
  data() {
    return {
      i: 0,
      animate: false,
      items: data.crew
    };
  },
  methods: {
    handleNavClick() {
      this.items.forEach((element, index) => {
        element.isActive = false;
      });
      this.animateChange();
    },
    animateChange() {
      this.animate = true;
      setTimeout(() => {
        this.animate = false;
      }, 1500);
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  display: grid;
  grid-template-columns: 1.75fr 1fr;
  padding-bottom: 100px;
  gap: 50px;
  @media only screen and (max-width: 1000px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
.section-one {
  display: flex;
  justify-content: end;
  @media only screen and (max-width: 1000px) {
    justify-content: center;
  }
}
.dest-img {
  padding-top: 60px;
  max-height: 450px;
  width: auto;
  @media only screen and (max-width: 1000px) {
    width: 80%;
    max-height: 100%;
    padding-left: 0px;
    max-width: 500px;
  }
}
nav {
  cursor: pointer;
  margin-bottom: 30px;
}
span {
  @include nav-text();
  margin-right: 30px;
  padding-bottom: 10px;
  &:hover {
    border-bottom: 2px solid $color-main;
  }
  @media only screen and (max-width: 1000px) {
    &:last-of-type {
      margin-right: 0px;
    }
  }
}
.active {
  border-bottom: 2px solid $color-light;
}
.section-two {
  padding-top: 80px;
}
.dest-info {
  padding-bottom: 60px;
  margin-bottom: 20px;
}
.dest-specs {
  display: flex;
  gap: 50px;
}
.fadeIn {
  animation: fadeIn 2s;
}
//Animateion testing
@keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
}
</style>
