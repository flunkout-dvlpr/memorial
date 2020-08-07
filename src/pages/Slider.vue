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
      slide: 1,
      slides: [
        {
          id: 1,
          imageLink: 'https://scontent.fhou1-2.fna.fbcdn.net/v/t1.0-9/117383277_2947683312010627_2696935639483858581_o.jpg?_nc_cat=106&_nc_sid=340051&_nc_ohc=Vlxw7yu-xTAAX9OI-DK&_nc_ht=scontent.fhou1-2.fna&oh=9ace5159a52cb2b7f7e1b9566ebf93d6&oe=5F54B2C8'
        },
        {
          id: 2,
          imageLink: 'https://scontent.fhou1-2.fna.fbcdn.net/v/t1.0-9/117294630_3358427504180712_2205901232245517998_n.jpg?_nc_cat=100&_nc_sid=8bfeb9&_nc_ohc=wSc0WH0xXR8AX_YPUIc&_nc_ht=scontent.fhou1-2.fna&oh=87c4b3461555f12e23f5956237010d83&oe=5F5239EE'
        }
      ]
    }
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
