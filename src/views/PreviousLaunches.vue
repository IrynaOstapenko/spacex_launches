<template>
  <div class="hero">

    <Navigation />

    <div class="error-message" v-if="error">{{ error }}</div>

    <LaunchCard
      v-for="(previousLaunch, index) in previousLaunches"
      :number="index + 1"
      :title="previousLaunch.title"
      :date="previousLaunch.date.toLocaleString()"
      :result="previousLaunch.result"
    />

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
    Footer,
  },
  data() {
    return {
      launches: [],
      previousLaunches: [],
      sortedPreviousLaunches: [],
      currentDate: new Date().getTime(),
      error: ''
    };
  },

  async created() {
    this.fetchLaunches();
  },

  methods: {
    async fetchLaunches() {
      const url = "https://api.spacexdata.com/v4/launches/";
      const response = await fetch(url);
      try {
        await this.handleResponse(response);
      } catch (error) {
        this.error = error.message;
      }
    },

    async handleResponse(response) {
      if (response.status >= 200 && response.status < 300) {
        const launchesAll = await response.json();
        this.launches = launchesAll.map((launch) => {
          return {
            title: launch.name,
            date: new Date(launch.date_utc),
            result: launch.success,
          };
        });
        this.previousLaunches = this.launches.filter((launch) => {
          return launch && new Date(launch.date).getTime() < this.currentDate;
        });
        this.previousLaunches.sort((a, b) => {
          return a.date - b.date;
        });
        return true;
      } else {
        if (response.status === 404) {
          throw new Error("Url not found");
        }
        if (response.status === 401) {
          throw new Error("Unauthorized");
        }
        if (response.status > 500) {
          throw new Error("Server error");
        }
        throw new Error("Something went wrong");
      }
    },
  },
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

.error-message {
  position: relative;
  color: white;
  font-size: 30px;
}
</style>

