<template>
  <b-modal :id="portfolio.id">
    <template #modal-title>
      <p class="text-dark">{{ portfolio.title }}</p>
    </template>
    <!-- Carousel -->
    <div>
        <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
        >

        <!-- Slides with image only -->
        <b-carousel-slide v-for="(photo, i) in photo" :key="i" :img-src="photo">
        </b-carousel-slide>

        </b-carousel>

        <!-- <p class="mt-4">
        Slide #: {{ slide }}<br>
        Sliding: {{ sliding }}
        </p> -->
    </div>
    <p class="my-4 text-dark">{{ portfolio.description }}</p>
  </b-modal>
</template>
<script>
export default {

  props: {
    portfolio: {
      type: Object,
      default() {
        return {}
      }
    },
    photo: {
        type: Array,
        default() {
            return []
        }
    }
  },
  data() {
      return {
        slide: 0,
        sliding: null
      }
    },
    methods: {
      onSlideStart(slide) {
        this.sliding = true
      },
      onSlideEnd(slide) {
        this.sliding = false
      }
    },
  computed: {
    localTask: {
      get () {
        return this.portfolio
      },
      set (newValue) {
        this.$emit('update:portfolio', newValue)
      }
    }
  }
}
</script>
