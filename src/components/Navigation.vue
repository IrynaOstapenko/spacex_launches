<template>
  <div class="navigation">

    <RouterLink :to="{ name: 'future' }" class="nav-image"
      ><img src="/images/white-shuttle.png" alt="white-shuttle"></RouterLink>

    <nav :class="{ visible: isOpen }">
      <RouterLink :to="{ name: 'future' }">Upcoming Launches</RouterLink>
      <RouterLink :to="{ name: 'previous' }">Previous Launches</RouterLink>
    </nav>
    
    <button class="hamburger-button" @click="toggleMenu()">
      <img src="/images/hamburger-button.png" alt="hamburger-menu-button" />
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.navigation {
  position: fixed;
  top: 0;
  height: 50px;
  width: 100%;
  background-color: black;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  align-items: center;
}

.nav-image {
  height: 40px;
  width: 40px;
  margin-right: 10%;
  margin-left: 5%;
}

nav {
  visibility: hidden;
  width: 50%;
  height: 150px;
  position: absolute;
  top: 50px;
  right: 0;
  padding-left: 5%;
  background-color: rgba(0, 0, 0, 0.721);
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-around;
  color: white;
  text-transform: uppercase;
  font-size: var(--mobile-font-size);
}

.visible {
  visibility: visible;
}

.invisible {
  visibility: hidden;
}

a {
  text-decoration: none;
  color: white;
}

a.router-link-active:not(.nav-image) {
  border-bottom: 1px solid white;
  width: 80%;
  padding-bottom: 5px;
}

.hamburger-button {
  display: block;
  margin-right: 5%;
}

@media only screen and (min-width: 768px) {
  .navigation {
    height: 80px;
    justify-content: flex-start;
  }

  .nav-image {
    height: 70px;
    width: 70px;
  }

  nav {
    visibility: visible;
    width: 100%;
    height: auto;
    position: relative;
    top: auto;
    right: auto;
    padding-left: 0;
    flex-flow: row nowrap;
    font-size: var(--font-size);
  }

  a.router-link-active:not(.nav-image) {
    width: auto;
  }

  .hamburger-button {
    display: none;
  }
}
</style>

