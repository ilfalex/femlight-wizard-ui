<template>
	<div class="swiper-slide">
    <h3>Hello</h3>
				<!-- <pagination/> -->

        <options-selector
          v-if="step === 0"
          step="0"
          param="anatomy"
          title="Step One: Choose Your Anatomy"
					subtitle="Choose the type of product you want to create."
          :options="$store.state.options.anatomies"/>

        <options-selector
          v-if="step === 1"
          step="1"
          param="sleve_cover"
          title="Step Two: Choose Your Sleve Cover"
          subtitle="This is where you will be able to choose your sleve cover"
          :options="$store.state.options.colors"/>

        <texture-selector
          v-if="step === 2"
          step="2"
          param="texture"
          title="Step Three: Choose Texture"
          subtitle="This is where you will be able to choose your sleve cover"
          :options="$store.state.options.textures"/>

        <options-selector
          v-if="step === 3"
          step="3"
          param="femlight_model"
          title="Step Four: Choose Femlight"
          subtitle="This is where you will be able to choose your sleve cover"
          :options="$store.state.options.form_factors"/>

        <media-uploader-dropzone
          v-if="step === 4"
          step="4"
          title="Step Five: Upload Anatomy"
          subtitle="This is where you will be able to choose your sleve cover"
          slug="upload-anatomy"/>

        <media-uploader-dropzone
        	 v-if="step === 5"
           step="5"
           title="Step Six: Upload Insignia"
           subtitle="This is where you will be able to choose your sleve cover"
           slug="upload-insignia"/>

        <confirm-order
        	 v-if="step === 6"
           step="6"
           title="Step Seven: Confirm Order"
           subtitle="This is where you will be able to choose your sleve cover"/>

	</div>
</template>

<script>

	export default {
		components: {
			OptionsSelector: require('./Utility/OptionsSelectorCard.vue'),
			TextureSelector: require('./Utility/TextureSelector.vue'),
			ConfirmOrder: require('./Steps/ConfirmOrder.vue'),
			MediaUploaderDropzone: require('./Utility/MediaUploaderDropzone.vue'),
			Pagination: require('./Pagination.vue')
		},
    mounted () {
      console.log(this)
    },
		computed: {
			step () {
				// return this.$store.state.step
			}
		}
	}
</script>
