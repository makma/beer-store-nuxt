<template>
  <div class="columns is-multiline">
    <div v-for="(beerItem) in beerItems" :key="beerItem.id" class="column is-one-third">
      <BeerItem :title="beerItem.title" :description="beerItem.description" :image-src="beerItem.imageSrc" :image-caption="beerItem.imageCaption" :source-url="beerItem.sourceUrl" />
    </div>
  </div>
</template>

<script>
import BeerItem from '~/components/BeerItem'

export default {
  name: 'BeerListing',

  components: {
    BeerItem
  },

  props: {
    beerItems: {
      type: Array,
      required: true
    }
  }
}
</script>
