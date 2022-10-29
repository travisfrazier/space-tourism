<template>
	<Layout class="destination">
		<DestItem />
	</Layout>
</template>

<script>
import DestItem from '../components/DestItem.vue';

export default {
	metaInfo: {
		title: 'Destination',
	},
	components: {
  		DestItem
	}
};
</script>

<style lang="scss" scoped>
.destination {
	background: url('../assets/images/destination.png');
	background-size: cover;
	background-position: center;
	background-repeat: no-repeat;
}
</style>
