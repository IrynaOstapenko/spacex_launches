<template>
    <div class="footer">&#169; Iryna Ostapenko, {{ currentYear }}</div>
</template>

<script>
    export default {
        data() {
            return {
                currentYear: new Date().getFullYear(),
            }

        }
    }
</script>

<style scoped>
    .footer {
        position: fixed;
        bottom: 0;
        width: 100vw;
        height: 45px;
        background: black;
        color: white;
        text-align: center;
        line-height: 45px;
    }
</style>
