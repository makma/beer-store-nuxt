<template>
  <section class="section">
    <h1 class="title">
      Available Beer
    </h1>
    <BeerListing :beer-items="beerItems" />
  </section>
</template>

<script>
import { DeliveryClient } from '@kentico/kontent-delivery'
import BeerListing from '~/components/BeerListing'

export default {
  name: 'HomePage',

  components: {
    BeerListing
  },

  data () {
    return {
      beerItems: []
    }
  },

  mounted () {
    this.getBeerItems()
  },

  methods: {
    getBeerItems () {
      const deliveryClient = new DeliveryClient({
        projectId: 'a8bbf063-f609-01e7-4870-223458b9b69d'
      })

      deliveryClient
        .items()
        .type('beer')
        .toPromise()
        .then((response) => {
          this.beerItems = response.items.map((item) => {
            return {
              id: item.system.id,
              title: item.title.value,
              description: item.description.value,
              sourceUrl: item.source.value,
              imageSrc: item.image.value[0].url,
              imageCaption: item.image.value[0].description
            }
          })
        })
    }
  }
}
</script>
