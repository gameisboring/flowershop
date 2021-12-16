<template>
  <header :class="{ 'scrolled-nav': scrolledNav }">
    <nav>
      <a class="branding" href="/">
        <img src="@/assets/logo.png" alt="" srcset="" />
      </a>
      <ul v-show="!mobile" class="navigation">
        <li>
          <router-link class="link" :to="{ name: 'Home' }">Home</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: 'About' }">About</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Portfolio' }"
            >Portfolio</router-link
          >
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Contact' }"
            >Contact</router-link
          >
        </li>
      </ul>
      <div class="icon">
        <i
          @click="toggleMobileNav"
          v-show="mobile"
          class="far fa-bars"
          :class="{ 'icon-active': mobileNav }"
        >
        </i>
      </div>
      <transition name="mobile-nav"
        ><ul v-show="mobileNav" class="dropdown-nav">
          <li>
            <router-link class="link" :to="{ name: 'Home' }">Home</router-link>
          </li>
          <li>
            <router-link class="link" :to="{ name: 'About' }"
              >About</router-link
            >
          </li>
          <li>
            <router-link class="link" :to="{ name: 'Portfolio' }"
              >Portfolio</router-link
            >
          </li>
          <li>
            <router-link class="link" :to="{ name: 'Contact' }"
              >Contact</router-link
            >
          </li>
        </ul></transition
      >
    </nav>
  </header>
</template>

<script>
export default {
  name: 'navigation',
  data() {
    return {
      scrolledNav: null,
      mobile: null,
      mobileNav: null,
      windowWidth: null,
    }
  },
  created() {
    window.addEventListener('resize', this.checkScreen)
    this.checkScreen()
  },
  mounted() {
    window.addEventListener('scroll', this.updateScroll)
  },
  methods: {
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav
    },
    checkScreen() {
      this.windowWidth = window.innerWidth
      if (this.windowWidth <= 768) {
        this.mobile = true
        return
      } else {
        this.mobile = false
        this.mobileNav = false
        return
      }
    },
    updateScroll() {
      const scrollPosition = window.scrollY
      if (scrollPosition > 50) {
        this.scrolledNav = true
        return
      } else {
        this.scrolledNav = false
      }
    },
  },
}
</script>

<style lang="css" scoped>
header {
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 99;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  transition: 0.5s ease all;
  color: #fff;
}

header nav {
  position: relative;
  display: flex;
  flex-direction: row;
  padding: 12px 0;
  transition: 0.5s ease all;
  width: 90%;
  margin: 0 auto;
}

@media (min-width: 1140px) {
  header nav {
    max-width: 1140px;
  }
}

header nav ul,
header nav .link {
  font-weight: 500;
  color: #fff;
  list-style: none;
  text-decoration: none;
}

header nav li {
  text-transform: uppercase;
  padding: 0 16px;
  margin-left: 16px;
}

header nav ul {
  padding: 0;
}

header nav .link {
  font-size: 16px;
  transition: 0.5s ease all;
  padding-bottom: 4px;
  border-bottom: 1px solid transparent;
}

header nav .navigation {
  display: flex;
  align-items: center;
  flex: 1;
  justify-content: end;
}

header nav .link:hover {
  color: #00afea;
  border-color: #00afea;
}

header .branding {
  display: flex;
  align-items: center;
}

header .branding img {
  width: 50px;
  transition: 0.5s ease all;
}

header .icon {
  display: flex;
  position: absolute;
  align-items: center;
  top: 0;
  right: 24px;
  height: 100%;
}

header .icon i {
  cursor: pointer;
  font-size: 24px;
  transition: 0.8s ease all;
}

header .icon-active {
  transform: rotate(90deg);
}

header .dropdown-nav {
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 100%;
  max-width: 250px;
  height: 100%;
  background-color: #fff;
  top: 0;
  left: 0;
  margin: 0;
}

header .dropdown-nav li {
  padding: 16px;
  margin-left: 0;
}

header .dropdown-nav li .link {
  color: black;
}

.mobile-nav-enter-active,
.mobile-nav-leave-active {
  transition: 1s ease all;
}

.mobile-nav-enter,
.mobile-nav-leave-to {
  transform: translateX(-250px);
}

.mobile-nav-enter-to {
  transform: translateX(0);
}

.scrolled-nav {
  background-color: #000;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.1);
}

.scrolled-nav nav .link {
  font-size: 14px;
}

.scrolled-nav nav .branding img {
  width: 40px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
    0 2px 4px -1px rgba(0, 0, 0, 0.1);
}
</style>
