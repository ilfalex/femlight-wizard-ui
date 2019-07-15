<template>
  <swiper-container/>
</template>

<script>
import SwiperContainer from '../SwiperContainer'
export default {
    components: {
      SwiperContainer
    },
    data: function () {
        return {
           message: 'Hello I am talking from the example component!'
        }
    },
    mounted() {
        console.log('Example Component mounted.')
    }
}
</script>
