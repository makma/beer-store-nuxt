<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title has-text-grey">
        {{ title }}
      </p>
    </header>
    <div class="card-content">
      <div class="content has-text-centered">
        <figure>
          <img
            :src="imageSrc"
          >
          <figcaption>{{ imageCaption }}</figcaption>
          <div class="card-content">
            {{ description }}
            <div>
              <a :href="sourceUrl" target="_blank">Source</a>
            </div>
          </div>
        </figure>
      </div>
    </div>
    <footer class="card-footer">
      <b-dropdown aria-role="list">
        <b-button slot="trigger" slot-scope="{ active }" size="is-medium" class="variants-button">
          <span>{{ selectedVariant.label }}</span>
          <b-icon :icon="active ? 'menu-up' : 'menu-down'" />
        </b-button>
        <b-dropdown-item v-for="(priceVariant) in priceVariants" :key="priceVariant.label" aria-role="listitem" @click="selectedVariant=priceVariant">
          {{ priceVariant.label }}
        </b-dropdown-item>
      </b-dropdown>
      <b-button
        class="card-footer-item is-primary snipcart-add-item"
        size="is-medium"
        icon-left="cart-plus"
        :data-item-id="id"
        data-item-price="0"
        :data-item-url="`${storeUrl}${this.$route.fullPath}`"
        :data-item-description="description"
        :data-item-image="`${imageSrc}?h=300`"
        :data-item-name="title"
        data-item-custom1-name="Variant"
        :data-item-custom1-options="formattedPriceOptions"
        :data-item-custom1-value="selectedVariant.label"
      >
        {{ `Buy $${selectedVariant.price}` }}
      </b-button>
    </footer>
  </div>
</template>

<script>
function formatPriceOptions (priceVariants) {
  let priceOptionsCustomData = ''
  priceVariants.map((priceVariant) => {
    priceOptionsCustomData = priceOptionsCustomData + `${priceVariant.label}[${priceVariant.price}]|`
  })

  // remove last |
  return priceOptionsCustomData.slice(0, -1)
}

export default {

  name: 'BeerItem',

  props: {
    id: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    imageSrc: {
      type: String,
      required: true
    },
    imageCaption: {
      type: String,
      required: true
    },
    sourceUrl: {
      type: String,
      required: true
    },
    price: {
      type: Number,
      required: true
    },
    priceVariants: {
      type: Array,
      required: true
    }
  },

  data () {
    return {
      storeUrl: process.env.NUXT_ENV_STORE_URL,
      formattedPriceOptions: formatPriceOptions(this.priceVariants),
      selectedVariant: this.priceVariants[0]
    }
  }
}
</script>

<style scoped>
.content figure {
    margin: 0;
}

.content figure img {
  height: 20rem;
}

.card-content {
  padding-top: 0.25rem;
  height: 100%;
}

.card {
   display: flex;
   flex-direction: column;
   height: 100%;
}

.card:hover {
  box-shadow: 8px 5px 22px -11px rgba(0,0,0,1);
}

.card-footer {
    display: flex;
    border-top: none;
}

.button {
  margin: 1rem;
}

.variants-button {
  width: 6rem;
}

</style>
