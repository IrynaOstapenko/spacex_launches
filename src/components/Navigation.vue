<template>
	<div class="navigation">
        <RouterLink :to="{ name: 'future' }" class="nav-image"><img src="/images/white-shuttle.png" alt="white-shuttle" /></RouterLink>
        <nav>
            <RouterLink :to="{ name: 'future' }">Upcoming Launches</RouterLink>
            <RouterLink :to="{ name: 'previous' }">Previous Launches</RouterLink>
        </nav>        
    </div>
</template>

<script>
export default {
	data() {
		
	}
}
</script>

<style scoped>
    .navigation {
        height: 115px;
        width: 100%;
        background-color: black;
        display: flex;
        flex-flow: row nowrap;
        justify-content: flex-start;
        align-items: center;
    }

    .nav-image {
        height: 70px;
        width: 70px;
        margin-right: 10%;
        margin-left: 5%;
    }

    nav {
        width: 100%;
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-around;
        color: white;
        text-transform: uppercase;
    }

    a {
        text-decoration: none;
        color: white;
    }

    a.router-link-active:not(.nav-image) {
        /* text-decoration: underline;
        text-underline-position: under; */
        border-bottom: 1px solid white; 
        padding-bottom: 5px;
    }
</style>

