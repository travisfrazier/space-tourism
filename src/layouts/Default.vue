<template>
	<div class="layout">
		<div class="wrapper">
			<Header />
		</div>
		<transition name="fade" appear>
			<div class="container">
				<slot />
			</div>
		</transition>
	</div>
</template>

<static-query>
query {
  metadata {
	siteName
  }
}
</static-query>

<script>
import Header from '../components/Header.vue';

export default {
	components: {
		Header
	}
}
</script>

<style lang="scss">
body {
	margin: 0;
	padding: 0;
	line-height: 1.5;
	color: $color-main;
}

.layout {
	//max-width: 760px;
	margin: 0 auto;
	padding-left: 0px;
	padding-right: 0px;
	padding-top: 40px;
	min-height: 100vh;
}

.container {
	padding: 40px 15px 0px;
	max-width: 1100px;
	margin: 0 auto;
}

.fade-enter-active {
  transition: opacity 1.5s;
}

.fade-enter {
  opacity: 0;
}
</style>
