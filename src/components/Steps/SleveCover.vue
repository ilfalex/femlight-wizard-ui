<template>
	<div >
		
		<wizard-nav-header
			:title="title"
			:subtitle="subtitle"/>

				<div class="row">
					<div
						v-for="item in options"
						class="col-lg-6 p-2">
							<card-block
								:param="'sleve_cover'"
								:item="item" />
					</div>
				</div>
	</div>
</template>

<script>
	import CardBlock from '../../components/Utility/CardBlock.vue'
	export default {
		props: {
			subtitle: String,
			title: String
		},
		components: {
			CardBlock
		},
		computed: {
			options () {
				return this.$store.state.options.colors
			}
		}
	}
</script>
