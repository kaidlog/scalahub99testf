<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
      <div class="hero-body has-text-centered">
        <p class="title mb-6">
          Welcome to ScalaHub
        </p>
        <p class="subtitle">
          台灣最具水準的貨艙一體公司
        </p>
      </div>
    </section>

    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">Let's get started!</h2>
        <h2 class="is-size-2 has-text-centered">&nbsp</h2>
        <div class="has-text-centered">
          <router-link to="/apply" class="button is-success">
            <span class="icon"><i class="fas fa-running"></i></span>
            <span>馬上體驗 </span>
          </router-link>
        </div>

      </div>

      <!--      <ProductBox -->
      <!--        v-for="product in latestProducts"-->
      <!--        v-bind:key="product.id"-->
      <!--        v-bind:product="product" />-->
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import ProductBox from '@/components/ProductBox'

export default {
  name: 'Home',
  data() {
    return {
      latestProducts: []
    }
  },
  components: {
    ProductBox
  },
  mounted() {
    this.getLatestProducts()

    document.title = 'Home | ScalaHub'
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading', true)

      await axios
          .get('/api/v1/latest-products/')
          .then(response => {
            this.latestProducts = response.data
          })
          .catch(error => {
            console.log(error)
          })

      this.$store.commit('setIsLoading', false)
    }
  }
}
</script>