<template>
  <div class="hero">
    <Navigation />
    <div>Previous launches</div>
	<Footer />
  </div>
</template>

<script>
import Navigation from "../components/Navigation.vue";
import LaunchCard from "../components/LaunchCard.vue";
import Footer from "../components/Footer.vue";

export default {
  components: {
    Navigation,
	LaunchCard,
	Footer
  },
  data() {},
};
</script>

<style scoped>
.hero {
  width: 100%;
  height: 100%;
  position: relative;
  padding-top: 90px;
  background-image: linear-gradient(rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)),
    url("/images/earth-satellite.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  overflow-x: hidden;
}
</style>

