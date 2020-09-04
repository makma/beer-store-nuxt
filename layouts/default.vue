<template>
  <div>
    <div id="snipcart" hidden data-api-key="YWRkYmExODUtNDlhYy00NmNlLTllY2YtY2ZiODU5MjczZGE3NjM3MzQ1NTc4MDEwOTE5ODcz" />
    <nav
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand">
        <a
          class="navbar-item"
          href="/"
        >
          Beer Store
        </a>

        <div class="navbar-burger">
          <span />
          <span />
          <span />
        </div>
      </div>
    </nav>

    <section class="main-content columns">
      <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">
          General
        </p>
        <ul class="menu-list">
          <li
            v-for="(item, key) of items"
            :key="key"
          >
            <nuxt-link
              :to="item.to"
              exact-active-class="is-active"
            >
              <b-icon :icon="item.icon" /> {{ item.title }}
            </nuxt-link>
          </li>
        </ul>
      </aside>

      <div class="container column is-10">
        <nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'Beer Offer',
          icon: 'beer',
          to: { name: 'index' }
        }
      ]
    }
  }
}
</script>

<style scoped>
.section {
  padding: 3rem 1.5rem 5rem 1.5rem;
}
</style>
