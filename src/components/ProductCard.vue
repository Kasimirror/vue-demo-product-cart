<template>
  <div class="card">
    <div class="card-title">
      {{ product.name }}
    </div>
    <div class="card-body">
      <!-- En löytänyt toimivaa ratkaisua dynaamiselle class nimikkeelle, toistaiseksi. -->
      <i @class="'icofont-10x icofont-' + icoFont()"></i>
      <form>
        <div class="row">
          <div class="cell">
            <label>Type:</label>
          </div>
          <div class="cell">
            <em>{{ product.type }}</em>
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Price:</label>
          </div>
          <div class="cell">
            ${{ product.price.USD }}
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Quantity:</label>
          </div>
          <div class="cell">
            <input type="number" v-model.number="quantity">
          </div>
        </div>
      </form>
    </div>
    <div class="card-footer">
      <button @click="addToCart(product.name, quantity)" class="btn btn-light">
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'ProductCard',
  props: ['product', 'index', 'addToCart', 'inventory'],
  data () {
    return {
      quantity: 0
    }
  },
  computed: {
    icoFont (name) {
      const product = this.inventory.name((p) => {
        return p.name === name
      })
      return product.name
    }
  }
}
</script>
