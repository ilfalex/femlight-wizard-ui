<template>
	<div>

    <wizard-nav-header
      :title="title"
      :subtitle="subtitle"
			:step="step"/>

			<drop-zone
				:ref="slug"
				:id="slug"
				:options="dropzoneOptions"
				@vdropzone-complete="uploadSuccess" />

	</div>
</template>

<script>
	import DropZone from 'vue2-dropzone'
	import 'vue2-dropzone/dist/vue2Dropzone.min.css'
  import WizardNavHeader from '../../components/Utility/WizardNavHeader.vue'

	export default {
    name: 'Uploader',
		props: {
      subtitle: String,
      title: String,
      slug: String,
      step: String,
      options: Array
		},
    components: {
			WizardNavHeader,
      DropZone
		},
		data: function () {
	    return {
	      dropzoneOptions: {
	          url: '/customize/design/upload/' + this.slug.replace('upload-', ''),
	          thumbnailWidth: 600,
						addRemoveLinks: true,
	          headers: {
							"X-CSRF-TOKEN": document.head.querySelector('meta[name="csrf-token"]').content
							// 'Authorization': 'Bearer ' + $('meta[name="api_token"]').attr('content'),
						}
	      }
	    }
	  },
		methods: {
			uploadSuccess(file, response) {
				this.$store.dispatch('updateProduct', {
					param: this.slug.replace('-', '_') + '_file',
					value: file.dataURL
				})

				this.$refs[this.slug].removeAllFiles();
				// continue to next step
				this.$store.dispatch('nextStep')
			}
		}
	}
</script>
