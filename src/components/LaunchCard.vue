<template>
  <div class="launch-card">
    <div class="sequence-number">{{ number }}</div>

    <div class="vertical-line"></div>

    <div class="launch-info">
      <div class="launch-info__title">{{ title }}</div>
      <div class="date-and-time-section">
        <button
          @click="
            isHidden = false;
            isActive = false;
          "
          :class="{ inactive: isHidden }"
        >
          Date
        </button>

        <div class="vertical-line-small"></div>
        <button
          @click="
            isActive = true;
            isHidden = true;
          "
          :class="{ inactive: !isActive }"
        >
          {{ timeLeft ? "Time left" : "Result" }}
        </button>
      </div>
      
      <div v-show="!isHidden" class="launch-info__date">{{ date }}</div>
      <div v-show="isActive" class="launch-info__time-left">
        {{ timeLeft ? calculateTime(timeLeft) : defineResult(result) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    number: Number,
    title: String,
    date: String,
    timeLeft: String,
    result: Boolean,
  },
  data() {
    return {
      isHidden: false,
      isActive: false,
    };
  },

  methods: {
    calculateTime(ms) {
      let days = Math.floor(ms / (24 * 60 * 60 * 1000));
      let daysms = ms % (24 * 60 * 60 * 1000);
      let hours = Math.floor(daysms / (60 * 60 * 1000));
      hours = hours <= 9 ? "0" + hours : hours;
      let hoursms = ms % (60 * 60 * 1000);
      let minutes = Math.floor(hoursms / (60 * 1000));
      minutes = minutes <= 9 ? "0" + minutes : minutes;
      let minutesms = ms % (60 * 1000);
      let sec = Math.floor(minutesms / 1000);
      sec = sec <= 9 ? "0" + sec : sec;
      return (
        "T-" + days + " " + "days" + " " + hours + ":" + minutes + ":" + sec
      );
    },
    defineResult(result) {
      if (result === true) {
        return "success";
      } else {
        return "fail";
      }
    },
  },
};
</script>

<style scoped>
.launch-card {
  height: 120px;
  width: 95%;
  margin-right: auto;
  margin-left: auto;
  background-color: black;
  color: white;
  margin-bottom: 20px;
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  align-items: center;
  padding-left: 40px;
  border-radius: 10px;
}

.sequence-number {
  font-size: 35px;
  margin-right: 40px;
}

.vertical-line {
  border-left: 2px solid white;
  height: 100px;
  margin-right: 40px;
}

.launch-info {
  height: 100px;
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
}

button {
  color: white;
}

.inactive {
  color: #b7b7b7;
}

.launch-info__title {
  font-size: 24px;
}

.date-and-time-section {
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  font-size: var(--mobile-font-size);
}

.vertical-line-small {
  border-left: 1px solid white;
  height: 20px;
  margin-right: 20px;
  margin-left: 20px;
}

.active {
  color: white;
}

.inactive {
  color: #b7b7b7;
}

.launch-info__date,
.launch-info__time-left {
  font-size: var(--mobile-font-size);
}

@media only screen and (min-width: 768px) {
  .launch-card {
    height: 170px;
    width: 90%;
  }

  .sequence-number {
    font-size: 50px;
  }

  .vertical-line {
    height: 140px;
  }

  .launch-info {
    height: 150px;
  }

  .launch-info__title {
    font-size: 36px;
  }

  .date-and-time-section {
    font-size: 24px;
  }

  .vertical-line-small {
    height: 24px;
    margin-right: 24px;
    margin-left: 24px;
  }

  .launch-info__date,
  .launch-info__time-left {
    font-size: 24px;
  }
}
</style>
