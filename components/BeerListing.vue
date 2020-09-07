<template>
  <div class="columns is-multiline">
    <div v-for="(beerItem) in beerItems" :key="beerItem.id" class="column is-half">
      <BeerItem
        :id="beerItem.id"
        :title="beerItem.title"
        :description="beerItem.description"
        :image-src="beerItem.imageSrc"
        :image-caption="beerItem.imageCaption"
        :source-url="beerItem.sourceUrl"
        :price-variants="beerItem.priceVariants"
      />
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
