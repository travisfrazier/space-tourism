<template>
	<Layout class="home">
		<main>
			<section class="section-one">
				<h5>SO, YOU WANT TO TRAVEL TO</h5>
				<h1>SPACE</h1>
				<p>
					Let’s face it; if you want to go to space, you might as well
					genuinely go to outer space and not hover kind of on the
					edge of it. Well sit back, and relax because we’ll give you
					a truly out of this world experience!
				</p>
			</section>
			<section class="section-two">
				<div>
					<g-link to="/destination/"><button class="home-btn">Explore</button></g-link>
				</div>
			</section>
		</main>
	</Layout>
</template>

<script>
export default {
	metaInfo: {
		title: 'Hello, world!',
	}
};
</script>

<style lang="scss" scoped>
.home {
	background: url('../assets/home/background-home-desktop.jpg');
	background-size: cover;
	background-repeat: no-repeat;
	background-position: center;
	height: 100vh;
	padding-bottom: 130px;
	@media only screen and (max-width: 768px) {
    	height: 100%;
  }
}
.home-btn {
	width: 275px;
	height: 275px;
	border-radius: 50%;
	@include heading-four;
	color: $color-night;
	cursor: pointer;
	transition: box-shadow 0.7s ease-in-out;
	&:hover {
		box-shadow: 0px 0px 0px 45px #9797976b;
		transition: box-shadow 0.7s ease-in-out;
	}
}
main {
	display: grid;
	grid-template-columns: 1fr 1fr;
	padding-right: 55px;
	padding-top: 120px;
	@media only screen and (max-width: 768px) {
    grid-template-columns: 1fr;
	padding-top: 60px;
	padding-right: 0px;
  }
}
.section-two {
	justify-self: end;
	align-self: end;
	@media only screen and (max-width: 768px) {
      justify-self: center;
	  margin-top: 50px;
  }
}
</style>
