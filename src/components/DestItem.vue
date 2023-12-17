<template>
  <main>
    <section class="section-one">
      <h5><strong>01</strong> Pick your destination</h5>
      <img
        class="dest-img"
        :class="{ fadeIn: animate }"
        :src="require('../assets/destination/' + this.items[this.i].images.webp)"
        width="500"
      />
    </section>
    <section class="section-two">
      <nav>
        <span
          v-on:click="
            i = 0;
            handleNavClick();
            items[0].isActive = true;
          "
          :class="{ active: this.items[0].isActive }"
          >Moon</span
        >
        <span
          v-on:click="
            i = 1;
            handleNavClick();
            items[1].isActive = true;
          "
          :class="{ active: this.items[1].isActive }"
          >Mars</span
        >
        <span
          v-on:click="
            i = 2;
            handleNavClick();
            items[2].isActive = true;
          "
          :class="{ active: this.items[2].isActive }"
          >Europa</span
        >
        <span
          v-on:click="
            i = 3;
            handleNavClick();
            items[3].isActive = true;
          "
          :class="{ active: this.items[3].isActive }"
          >Titan</span
        >
      </nav>
      <div :class="{ fadeIn: animate }">
        <h2>{{ this.items[this.i].name }}</h2>
        <p class="dest-info">
          {{ this.items[this.i].description }}
        </p>
        <div class="dest-specs">
          <div>
            <p>AVG. DISTANCE</p>
            <h5>{{ this.items[this.i].distance }}</h5>
          </div>
          <div>
            <p>EST. TRAVEL TIME</p>
            <h5>{{ this.items[this.i].travel }}</h5>
          </div>
        </div>
      </div>
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
      items: data.destinations
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
  grid-template-columns: 1fr 1fr;
  padding-bottom: 100px;
  gap: 50px;
  @media only screen and (max-width: 1000px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
.dest-img {
  padding-top: 60px;
  padding-left: 30px;
  @media only screen and (max-width: 1000px) {
    width: 100%;
    padding-left: 0px;
    max-width: 500px;
  }
}
h5 {
  color: $color-light;
  strong {
    color: $color-main;
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
}
.active {
  border-bottom: 2px solid $color-light;
}
.section-two {
  padding-top: 80px;
  @media only screen and (max-width: 1000px) {
    padding-top: 20px;
  }
}
.dest-info {
  border-bottom: 1px solid $color-main;
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
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>