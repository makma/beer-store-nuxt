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
      <button class="card-footer-item button is-primary">
        Add to cart
      </button>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'BeerItem',
  props: {
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
    }
  }
}
</script>

<style scoped>
.content figure {
    margin: 0;
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

.cart-footer {
    margin-top: auto;
}

</style>
