<template>
	<AppHeader />
	<div class="my-gap"></div>
	<div class="my-space">
		<AppFilter class="p-3"  @newSearch="getData"/>
		<AppMain />
	</div>
</template>

<script>
import AppFilter from './components/AppFilter.vue'
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'
import { cards } from './data/store'
import axios from 'axios'
export default {
	name: 'app',

	components: {
		AppHeader,
		AppFilter,
		AppMain,
	},

	data() {
		return {
			cards
		}
	},

	methods: {
		getData() {
			const url = cards.basepath + cards.endpoint;
			let options = {};
			let params = {}

			for (let key in cards.search) {
				if (cards.search[key]) {
					params[key] = cards.search[key]
					console.log('ciao')
				}
				if (Object.keys(params).length > 0) {
					options.params = params;
				}
				axios.get(url, options).then((res) => {
					cards.cardsList = res.data.data
					console.log(cards);
					
				});
			}
		}
	},

	mounted() {
		cards.endpoint = 'cardinfo.php?num=200&offset=0';
		this.getData();
	}
}
</script>

<style lang="scss" scoped>
.my-gap {
	height: 170px;
}

.my-space {
	max-width: 1200px;
	margin: 100px auto;
}
</style>

<!-- 

		<div class="" v-for="card  in cards.cardsList" :key="card.id">
			<p>
				{{ card.name }}
			</p>
			<img :src="card.card_images[0].image_url" alt="">
		</div>


	    "data": [
        {
            "id": 34541863,
            "name": "\"A\" Cell Breeding Device",
            "type": "Spell Card",
            "frameType": "spell",
            "desc": "During each of your Standby Phases, put 1 A-Counter on 1 face-up monster your opponent controls.",
            "race": "Continuous",
            "archetype": "Alien",
            "card_sets": [
                {
                    "set_name": "Force of the Breaker",
                    "set_code": "FOTB-EN043",
                    "set_rarity": "Common",
                    "set_rarity_code": "(C)",
                    "set_price": "1.31"
                }
            ],
            "card_images": [
                {
                    "id": 34541863,
                    "image_url": "https://images.ygoprodeck.com/images/cards/34541863.jpg",
                    "image_url_small": "https://images.ygoprodeck.com/images/cards_small/34541863.jpg",
                    "image_url_cropped": "https://images.ygoprodeck.com/images/cards_cropped/34541863.jpg"
                }
            ],
            "card_prices": [
                {
                    "cardmarket_price": "0.12",
                    "tcgplayer_price": "0.16",
                    "ebay_price": "4.99",
                    "amazon_price": "24.45",
                    "coolstuffinc_price": "0.25"
                }
            ]
        },
 -->