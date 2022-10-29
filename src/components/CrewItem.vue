<template>
  <main>
    <section class="section-two">
      <div :class="{ fadeIn: animate }">
        <h4>{{ this.items[this.i].title }}</h4>
        <h3>{{ this.items[this.i].name }}</h3>
        <p class="dest-info">
          {{ this.items[this.i].info }}
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
        :src="require('../assets/images/' + this.items[this.i].img)"
        width="500"
      />
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
          title: 'Commander',
          name: "Douglas Hurley",
          img: "douglas.svg",
          info: "Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.",
          isActive: true,
        },
        {
          title: 'Mission Specialist',
          name: "MARK SHUTTLEWORTH",
          img: "mark.svg",
          info: "Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.",
          isActive: false,
        },
        {
          title: 'Pilot',
          name: "Victor Glover",
          img: "victor.svg",
          info: "Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.",
          isActive: false,
        },
        {
          title: 'Flight Engineer',
          name: "Anousheh Ansari",
          img: "anousheh.svg",
          info: "Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.",
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
  grid-template-columns: 1.5fr 1fr;
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
  width: 100%;
  @media only screen and (max-width: 768px) {
    width: 100%;
    padding-left: 0px;
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
  @media only screen and (max-width: 768px) {
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
