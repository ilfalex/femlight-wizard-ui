<template>
  <div>

		<wizard-nav-header
			:title="title"
			:subtitle="subtitle"
			:step="step"/>


    <div class="preview-area">
      <!-- {{ selectedOption }} -->
      <div
        v-if="!selectedPreview"
        class="preview-box box bg-secondary text-center rounded mb-5"
        style="height:256px;">
        <p class="text-white">Select an Texture to preview..</p>
      </div>
      <div
        v-if="selectedPreview"
        class="details mb-5">
        <img
          :src="selectedPreview.img_path"
          class="img-fluid rounded"
          style="height:256px;">
      </div>
    </div>

    <carousel
      :per-page="4"
      :navigation-enabled="true">
      <slide
        v-if="item.img_path"
        v-for="item in options"
        :key="item.id">
        <div
          @click="setSelection(item)"
          @mouseover="">
          <card-block
            :param="param"
            :item="item"
            :hide-button="true"
            :is-selected="(selectedOption && item.id === selectedPreview.id)"/>
        </div>
      </slide>
    </carousel>


    <!-- <div class="container">
      <div class="row">
        <div
          v-for="item in options"
          class="col-md-6 col-lg-4 p-2">
            <div @click="setSelection(item)">
              <card-block
                :param="param"
                :item="item"
                :hide-button="true"/>
            </div>
              <div class="text-center flex">
                <button
                  class="btn btn-default bg-green text-white rounded mb-2"
                  @click="setSelection(item)">Select</button>
              </div>
        </div>
      </div>
    </div> -->

  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';
export default {
  props: {
    subtitle: String,
    title: String,
    param: String,
    options: Array,
    step: String
  },
  data: () => {
    return {
      selectedOption: null,
      selectedPreview: null
    }
  },
  components: {
    CardBlock: require('../../components/Utility/CardBlock.vue'),
    WizardNavHeader: require('../../components/Utility/WizardNavHeader.vue'),
    Carousel,
    Slide
    // WizardNavHeader
  },
  methods: {
    setSelection (item) {
      this.selectedOption = item
      this.setPreview(item)
      this.updateProduct(this.param, item)
    },
    setPreview (item) {
      this.selectedPreview = item
    },
    updateProduct(param, value) {
      // alert('editing the product')
      this.$store.dispatch('updateProduct', {
        param: param,
        value: value
      })
      // this.$store.dispatch('nextStep')
    }
  }
}
</script>


<style>
  .preview-box {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
