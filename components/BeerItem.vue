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
      <button
        class="card-footer-item button is-primary snipcart-add-item"
        :data-item-id="id"
        :data-item-price="price"
        :data-item-url="`${storeUrl}${this.$route.fullPath}`"
        :data-item-description="description"
        :data-item-image="`${imageSrc}?h=300`"
        :data-item-name="title"
      >
        Add to cart
      </button>
    </footer>
  </div>
</template>

<script>
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
    }
  },

  data () {
    return {
      storeUrl: process.env.storeUrl
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

.cart-footer {
    margin-top: auto;
}

</style>
