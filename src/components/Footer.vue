<template>
  <div class="footer">&#169; Iryna Ostapenko, {{ currentYear }}</div>
</template>

<script>
export default {
  data() {
    return {
      currentYear: new Date().getFullYear(),
    };
  },
};
</script>

<style scoped>
.footer {
  position: fixed;
  bottom: 0;
  width: 100vw;
  height: 25px;
  background: black;
  color: white;
  font-size: 14px;
  text-align: center;
  line-height: 25px;
}

@media only screen and (min-width: 768px) {
  .footer {
    height: 45px;
    font-size: var(--font-size);
    line-height: 45px;
  }
}
</style>
