<template>
  <main>
    <section class="section-two">
      <div class="section-content" :class="{ fadeIn: animate }">
        <div>
          <h5>The terminology...</h5>
          <h3>{{ this.items[this.i].name }}</h3>
          <p class="dest-info">
            {{ this.items[this.i].description }}
          </p>
        </div>
        <nav>
          <button
            v-on:click="
              i = 0;
              handleNavClick();
              items[0].isActive = true;
            "
            :class="{ active: this.items[0].isActive }"
            >1</button
          >
          <button
            v-on:click="
              i = 1;
              handleNavClick();
              items[1].isActive = true;
            "
            :class="{ active: this.items[1].isActive }"
            >2</button
          >
          <button
            v-on:click="
              i = 2;
              handleNavClick();
              items[2].isActive = true;
            "
            :class="{ active: this.items[2].isActive }"
            >3</button
          >
        </nav>
      </div>
    </section>
    <section class="section-one">
      <img
        class="dest-img"
        :class="{ fadeIn: animate }"
        :src="require('../assets/technology/' + this.items[this.i].images.portrait)"
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
      items: data.technology
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
  grid-template-columns: 1.5fr 1fr;
  padding-bottom: 100px;
  gap: 50px;
  @media only screen and (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
.dest-img {
  padding-top: 60px;
  width: 100%;
}
nav {
  cursor: pointer;
  margin-bottom: 30px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  margin-right: 30px;
}
button {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 1px solid $color-light;
  @include nav-text;
  color: $color-light;
  cursor: pointer;
  transition: background-color 0.7s ease-in-out;
  background-color: transparent;
  &:hover {
    background-color: $color-main;
    transition: background-color 0.7s ease-in-out;
    color: $color-night;
  }
  @media only screen and (max-width: 768px) {
    width: 60px;
    height: 60px;
  }
}
.active {
  background-color: $color-light;
  color: $color-night;
}
.section-two {
  padding-top: 80px;
}
.dest-info {
  padding-bottom: 60px;
  margin-bottom: 20px;
  @media only screen and (max-width: 768px) {
    padding-bottom: 0px;
  }
}
.dest-specs {
  display: flex;
  gap: 50px;
}
.fadeIn {
  animation: fadeIn 2s;
}
.section-content {
  display: flex;
  flex-direction: row-reverse;
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
