<template>
	<div>

        This is where you choose your Texture
				<div class="row">
					<div
						v-for="item in options"
						class="col-lg-6 p-2">
							<card-block
								:param="'texture'"
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
				return this.$store.state.options.textures
			}
		}
	}
</script>
