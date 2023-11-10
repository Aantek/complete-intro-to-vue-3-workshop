<template>
	<h1>Statistics</h1>

	<h1> {{ incrementTitle }} </h1>
	<p>{{ count }}</p>
	<p>{{ displayTitle }}</p>
	<p>{{ optimizedIncrementAmount }}</p>
	<button @click="incrementCount">Increment counting</button>
	<div>
		<label for="incrementAmount">Increment by: </label>
		<input type="number" v-model="incrementAmount"/>
	</div>
	<hr />
	<span v-for="(character, index) in characters" :key="`comma-list-character-${index}`">
	  {{ character.name }}{{ index === characters.length - 1 ? '' : ', ' }}
	</span>
</template>

<script>
export default {
	data () {
		return {
			count: 10,
			incrementAmount: 8,
			incrementTitle: 'Counter Standard',
			
			
		}
	},
	props: ["characters"],
	computed: {
		displayTitle() {
			if (this.count > 20) {
				return 'Counter Standard - very long'
			}
			else {
				return 'Counter Standard'
			}
		},
		optimizedIncrementAmount() {
			return this.displayTitle.length * this.incrementAmount
		},
		banderStatistics() {

			const elements = ['Air', 'Earth', 'Fire', 'Water']

			const statistics = {
				Air: 0,
				Earth: 0,
				Water: 0,
				Fire: 0
			}

			this.characters.forEach(character => {
				elements.forEach(element => {
					if (character.element.indexOf(element) > -1) {
						statistics[element] += 1
					}
				})
			})

			return statistics
		}
	},
	methods: {

		incrementCount() {
			this.count += this.optimizedIncrementAmount;
		},

	},

}
</script>

<style>

</style>