<template>
	<div>

        This is where you customize your Femlight
				<div class="row">
					<div
						v-for="item in options"
						class="col-lg-6 p-2">
							<card-block
								:param="'femlight_model'"
								:item="item" />
					</div>
				</div>

	</div>
</template>

<script>
	import CardBlock from '../../components/Utility/CardBlock.vue'
	export default {
		props: {
		},
		components: {
			CardBlock
		},
		computed: {
			options () {
				return this.$store.state.options.form_factors
			}
		}
	}
</script>
