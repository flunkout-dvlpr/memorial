<template>
  <div class="q-gutter-md">
    <q-carousel
      v-model="slide"
      transition-prev="scale"
      transition-next="scale"
      swipeable
      animated
      infinite
      control-color="accent"
      padding
      arrows
      :autoplay="2500"
      height="300px"
      class="bg-secondary text-accent shadow-1"
    >
      <q-carousel-slide
        class="column no-wrap flex-center"
        v-for="slide in slides"
        :key="slide.id"
        :name="slide.id"
      >
      <div class="q-ma-md">
          <img
            :src="slide.imageLink"
            class="contain-img"
          />
      </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<script>
export default {
  name: 'Slider',
  data () {
    return {
      slide: '1.jpg',
      slides: []
    }
  },
  created () {
    return this.$axios.get('images/get').then((response) => {
      if (response.data.type === 'success') {
        this.slides = response.data.payload
        console.log(response.data.payload)
      }
    })
  }
}
</script>

<style lang="scss">
  .contain-img {
    width: auto;
    height: 250px;
    border: 10px solid $accent;
    object-fit: contain;
  }
</style>
