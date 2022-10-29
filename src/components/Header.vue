<template>
  <header class="header">
    <strong>
      <g-image src="~/assets/images/nav-star.svg" width="500" />
    </strong>
    <div class="mobile-menu-container">
      <div
        v-on:click="toggleMenu"
        class="mobile-menu"
        :class="{ change: isVisible }"
      >
        <div class="bar1"></div>
        <div class="bar2"></div>
        <div class="bar3"></div>
      </div>
    </div>
    <nav class="nav">
      <g-link class="nav__link" to="/"><strong>00</strong>Home</g-link>
      <g-link class="nav__link" to="/destination/"
        ><strong>01</strong>Destination</g-link
      >
      <g-link class="nav__link" to="/crew/"><strong>02</strong>Crew</g-link>
      <g-link class="nav__link" to="/technology/"
        ><strong>03</strong>Technology</g-link
      >
    </nav>
    <nav v-bind:class="{ visible: isVisible }" class="mobile-nav">
      <div>
        <g-link class="nav__link" to="/"><strong>00</strong>Home</g-link>
        <g-link class="nav__link" to="/destination/"
          ><strong>01</strong>Destination</g-link
        >
        <g-link class="nav__link" to="/crew/"><strong>02</strong>Crew</g-link>
        <g-link class="nav__link" to="/technology/"
          ><strong>03</strong>Technology</g-link
        >
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      i: 0,
      isVisible: false,
      navItems: [
        {
          title: "Home",
          isActive: false,
        },
        {
          title: "Destination",
          isActive: false,
        },
        {
          title: "Crew",
          isActive: false,
        },
        {
          title: "Technology",
          isActive: false,
        },
      ],
    };
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
      this.isVisible = !this.isVisible;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
  padding-left: 40px;
  img {
    @media only screen and (max-width: 768px) {
      position: absolute;
      top: 15px;
      left: 10px;
	  width: 40px;
    }
  }
}

.nav {
  background: rgba(255, 255, 255, 0.04);
  backdrop-filter: blur(81.5485px);
  height: 96px;
  width: 896px;
  display: flex;
  align-items: center;
  justify-content: center;
  @media only screen and (max-width: 768px) {
    display: none;
  }
}

.nav__link {
  margin-left: 48px;
  text-decoration: none;
  height: 100%;
  display: flex;
  align-items: center;
  @include nav-text();
  @media only screen and (max-width: 768px) {
		width: 150px;
    margin-bottom: 5px;
	}
  strong {
    margin-right: 10px;
  }
  &:first-of-type {
    margin-left: 0px;
	@media only screen and (max-width: 768px) {
		margin-left: 48px;
	}
  }
  &:hover {
    border-bottom: 2px solid $color-main;
  }
}
.active--exact {
  border-bottom: 2px solid $color-light;
}
//Mobile Nav
.mobile-nav {
  position: fixed;
  left: 0;
  top: 0;
  transform: translate3d(0, -100vh, 0);
  width: 100vw;
  transition: transform 0.5s;
  max-width: 100%;
  background: rgba(255, 255, 255, 0.04);
  div {
    padding: 60px 0px 10px;
    width: 95%;
    margin-left: auto;
    margin-right: auto;
  }
}
.mobile-nav.visible {
  transform: translate3d(0, 0, 0);
  z-index: 999;
}
.mobile-menu-container {
  z-index: 1000;
  display: none !important;
  position: fixed;
  top: 1rem;
  right: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  @media only screen and (max-width: 768px) {
    display: flex !important;
  }
}
.mobile-menu {
  z-index: 998;
  display: none;
  @media only screen and (max-width: 768px) {
    display: inline-block;
    cursor: pointer;
  }
  .bar1,
  .bar2,
  .bar3 {
    width: 35px;
    height: 5px;
    background-color: #fff;
    margin: 6px 0;
    transition: 0.4s;
  }
  /* Rotate first bar */
  .hamburger {
    color: red;
  }
  &.change {
    .bar1 {
      -webkit-transform: rotate(-45deg) translate(-9px, 6px);
      transform: rotate(-45deg) translate(-9px, 6px);
    }
    /* Fade out the second bar */
    .bar2 {
      opacity: 0;
    }
    /* Rotate last bar */
    .bar3 {
      -webkit-transform: rotate(45deg) translate(-8px, -8px);
      transform: rotate(45deg) translate(-8px, -8px);
    }
  }
}
</style>
