<template>
	<Layout class="technology">
	    <h5><strong>03</strong> Space Launch 101</h5>
		<TechItem />
	</Layout>
</template>

<script>
import TechItem from '../components/TechItem.vue';

export default {
	metaInfo: {
		title: 'Technology',
	},
	components: {
  		TechItem
	}
};
</script>

<style lang="scss" scoped>
.technology {
	background: url('../assets/images/technology.png');
	background-size: cover;
	background-position: center;
	background-repeat: no-repeat;
}
</style>