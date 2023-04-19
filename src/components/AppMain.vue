<template>
	<main class="p-3">
		<div class="d-flex justify-content-center flex-wrap gap-3">
			<div class="card myCard justify-content-between align-item-center gap-0" v-for="card in cards.cardsList" :key="card.id">
				<div class="text-center text-uppercase text-white">
					<span>{{ card.name }}</span>
				</div>
				<div class="text-center text-secondary">
					<span>{{ card.type }}</span>
				</div>
				<div class="align-self-center">
					<img :src="card.card_images[0].image_url_small" :alt="card.name">
				</div>
			</div>
		</div>
	</main>
</template>

<script>
import { cards } from '../data/store';

export default {
	name: 'AppMain',
	data() {
		return {
			cards
		}
	},
}
</script>

<style lang="scss" scoped>

main{
	background-color: white;
	margin-bottom: 30px;
}
.myCard{
	background-color: orange;
	margin-bottom: 10px;
	width: calc(100% / 5 - 50px);
	height: 350px;
}

@media screen and (min-width:1200px) {
	.myCard{
	width: calc(100% / 3 - 100px);
	height: 350px;
}
}

@media screen and (min-width:768px) {
	.myCard{
	width: calc(100% / 2 - 200px);
	height: 350px;
}
}

@media screen and (max-width:768px) {
	.myCard{
	width: calc(100% / 1 - 80px);
	height: 350px;
}
}
</style>