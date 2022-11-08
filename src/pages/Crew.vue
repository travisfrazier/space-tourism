<template>
	<Layout class="crew">
		<h5><strong>02</strong> Meet Your Crew</h5>
		<CrewItem />
	</Layout>
</template>

<script>
import CrewItem from '../components/CrewItem.vue';

    export default {
        components: {
			CrewItem
		}
    }
</script>

<style lang="scss" scoped>
.crew {
	background: url('../assets/crew/background-crew-desktop.jpg');
	background-size: cover;
	background-position: center;
	background-repeat: no-repeat;
}
h5 {
  color: $color-light;
  strong {
    color: $color-main;
  }
}
</style>