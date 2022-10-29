<template>
  <main>
    <section class="section-one">
      <h5><strong>01</strong> Pick your destination</h5>
      <img
        class="dest-img"
        :class="{ fadeIn: animate }"
        :src="require('../assets/images/' + this.items[this.i].img)"
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
        <h2>{{ this.items[this.i].title }}</h2>
        <p class="dest-info">
          {{ this.items[this.i].info }}
        </p>
        <div class="dest-specs">
          <div>
            <p>AVG. DISTANCE</p>
            <h5>{{ this.items[this.i].specs.dist }}</h5>
          </div>
          <div>
            <p>EST. TRAVEL TIME</p>
            <h5>{{ this.items[this.i].specs.time }}</h5>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      i: 0,
      animate: false,
      items: [
        {
          title: "Moon",
          img: "moon.svg",
          info: "See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.",
          specs: {
            dist: "384,400 KM",
            time: "3 DAYS",
          },
          isActive: true,
        },
        {
          title: "Mars",
          img: "mars.svg",
          info: "Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!",
          specs: {
            dist: "225 MIL. KM",
            time: "9 MONTHS",
          },
          isActive: false,
        },
        {
          title: "Europa",
          img: "europa.svg",
          info: "The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.",
          specs: {
            dist: "628 MIL. KM",
            time: "3 YEARS",
          },
          isActive: false,
        },
        {
          title: "Titan",
          img: "titan.svg",
          info: "The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.",
          specs: {
            dist: "1.6 BIL. KM",
            time: "7 YEARS",
          },
          isActive: false,
        },
      ],
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
  @media only screen and (max-width: 768px) {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
.destination {
  background: url("../assets/images/destination.png");
  background-size: cover;
  //height: 100vh;
  background-position: center;
  background-repeat: no-repeat;
}
.dest-img {
  padding-top: 60px;
  padding-left: 30px;
  @media only screen and (max-width: 768px) {
    width: 100%;
    padding-left: 0px;
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
  @media only screen and (max-width: 768px) {
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
