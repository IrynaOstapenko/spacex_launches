<template>
  <div class="launch-card">
    <div class="sequence-number">{{ number }}</div>
    <div class="vertical-line"></div>
    <div class="launch-info">
      <div class="launch-info__title">{{ title }}</div>
      <div class="date-and-time-section">
        <div>Date</div>
        <div class="vertical-line-small"></div>
        <div>Time left</div>
      </div>
      <div class="launch-info__date">{{ date }}</div>
      <div class="launch-info__time-left">{{ timeLeft }}</div>
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
  },
};
</script>

<style scoped>
.launch-card {
  height: 170px;
  width: 90%;
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
}

.sequence-number {
  font-size: 50px;
  margin-right: 40px;
}

.vertical-line {
  border-left: 2px solid white;
  height: 140px;
  margin-right: 40px;
}

.launch-info {
  height: 150px;
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
}

.launch-info__title {
  font-size: 36px;
}

.date-and-time-section {
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
}

.vertical-line-small {
  border-left: 1px solid white;
  height: 24px;
  margin-right: 24px;
  margin-left: 24px;
}
</style>
