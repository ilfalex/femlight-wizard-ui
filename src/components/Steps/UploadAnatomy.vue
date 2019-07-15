<template>
	<div>

        This is where you upload your anatomy

				<drop-zone
					ref="myVueDropzone"
					id="upload-anatomy"
					:options="dropzoneOptions" />

	</div>
</template>

<script>
	import DropZone from 'vue2-dropzone'
	import 'vue2-dropzone/dist/vue2Dropzone.min.css'
	export default {
		props: {
		},
		data: function () {
	    return {
	      dropzoneOptions: {
	          url: 'https://httpbin.org/post',
	          thumbnailWidth: 150,
	          maxFilesize: 0.5,
	          headers: { "My-Awesome-Header": "header value" }
	      }
	    }
	  },
		mounted () {},
		components: {
			DropZone
		},
		methods: {}
	}
</script>
