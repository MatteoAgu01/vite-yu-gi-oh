<template>
	<header class="w-100">
		<div class="d-flex flex-column align-items-center flex-lg-row">
			<div class="px-3">
				<img id="logoYuGiOh" src="../../public/img/dowload.jpeg" alt="logo">
			</div>

			<div>
				<h1 class="text-capitalize">
					yu-gi-oh <span class="text-uppercase">api</span>
				</h1>
			</div>
		</div>
	</header>
</template>

<script>
export default {
	name: 'AppHeader',
}
</script>

<style lang="scss" scoped>
header {
	background-color: white;
	position: fixed;
	top: 0px;
	padding: 1%;
	z-index: 1000;
}

#logoYuGiOh {
	scale: 80%;

}

@media screen and (max-width:768px) {
	#logoYuGiOh {
		width: 200px;
	}
}
</style>