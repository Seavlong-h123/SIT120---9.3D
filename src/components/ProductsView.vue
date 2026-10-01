<template>

  <div class="page">

    <section class="page-banner">

      <span class="eyebrow">
        Hun Dy Electronics
      </span>

      <h1>
        Products
      </h1>

      <p>
        Browse appliances by category, brand,
        price and capacity.
      </p>

    </section>


    <section class="products-layout">

      <!-- FILTERS -->
      <aside class="filter-panel">

        <h3>
          Search & Filters
        </h3>


        <label>
          Search products

          <input
            v-model="search"
            type="text"
            placeholder="Search..."
          />

        </label>


        <label>
          Category

          <select v-model="category">

            <option value="All">
              All categories
            </option>

            <option
              v-for="item in categories"
              :key="item"
              :value="item"
            >
              {{ item }}
            </option>

          </select>

        </label>


        <label>
          Brand

          <select v-model="brand">

            <option value="All">
              All brands
            </option>

            <option
              v-for="item in brands"
              :key="item"
              :value="item"
            >
              {{ item }}
            </option>

          </select>

        </label>


        <label>
          Price

          <select v-model="priceRange">

            <option value="All">
              All prices
            </option>

            <option value="under500">
              Under $500
            </option>

            <option value="500to1000">
              $500 - $1000
            </option>

            <option value="over1000">
              Over $1000
            </option>

          </select>

        </label>


        <label>
          Capacity

          <select v-model="capacity">

            <option value="All">
              All sizes
            </option>

            <option value="Small">
              Small
            </option>

            <option value="Medium">
              Medium
            </option>

            <option value="Large">
              Large
            </option>

          </select>

        </label>


        <button
          class="btn btn-outline full"
          type="button"
          @click="resetFilters"
        >
          Reset Filters
        </button>

      </aside>


      <!-- PRODUCTS -->
      <div>

        <div class="results-header">

          <div>

            <h2>
              Product Results
            </h2>

            <p>
              {{ filteredProducts.length }}
              product(s) found.
            </p>

          </div>

        </div>


        <div
          v-if="filteredProducts.length > 0"
          class="product-grid"
        >

          <article
            v-for="product in filteredProducts"
            :key="product.id"
            class="product-card"
          >

            <div class="product-image">
              {{ product.icon }}
            </div>

            <div class="product-body">

              <span class="product-brand">
                {{ product.brand }}
              </span>

              <h3>
                {{ product.name }}
              </h3>

              <p>
                {{ product.features }}
              </p>

              <p>
                Capacity:
                <strong>
                  {{ product.capacity }}
                </strong>
              </p>

              <div class="product-meta">

                <strong>
                  ${{ product.price }}
                </strong>

                <span
                  :class="
                    product.stock === 'In stock'
                      ? 'in-stock'
                      : 'low-stock'
                  "
                >
                  {{ product.stock }}
                </span>

              </div>

              <button
                class="btn btn-small"
                type="button"
                @click="$emit('navigate', 'contact')"
              >
                Ask About This Product
              </button>

            </div>

          </article>

        </div>


        <div
          v-else
          class="empty-state"
        >

          <h3>
            No products found
          </h3>

          <p>
            Try changing your search or filters.
          </p>

        </div>

      </div>

    </section>

  </div>

</template>


<script setup>

import { computed, ref } from 'vue'

defineEmits(['navigate'])


const categories = [
  'Fridges',
  'Washing Machines',
  'TVs',
  'Kitchen Appliances'
]


const brands = [
  'Samsung',
  'LG',
  'Gree',
  'Panasonic'
]


const search = ref('')
const category = ref('All')
const brand = ref('All')
const priceRange = ref('All')
const capacity = ref('All')


const products = [

  {
    id: 1,
    icon: '▣',
    brand: 'Samsung',
    name: 'Twin Cooling Refrigerator',
    category: 'Fridges',
    price: 899,
    capacity: 'Large',
    features: 'Twin cooling',
    stock: 'In stock'
  },

  {
    id: 2,
    icon: '▣',
    brand: 'LG',
    name: 'Smart Inverter Fridge',
    category: 'Fridges',
    price: 749,
    capacity: 'Medium',
    features: 'Smart inverter',
    stock: 'In stock'
  },

  {
    id: 3,
    icon: '◫',
    brand: 'Samsung',
    name: 'Front Load Washer',
    category: 'Washing Machines',
    price: 699,
    capacity: 'Large',
    features: '8kg capacity',
    stock: 'In stock'
  },

  {
    id: 4,
    icon: '◫',
    brand: 'LG',
    name: 'Eco Wash Machine',
    category: 'Washing Machines',
    price: 499,
    capacity: 'Medium',
    features: 'Energy saving',
    stock: 'Low stock'
  },

  {
    id: 5,
    icon: '▤',
    brand: 'Samsung',
    name: 'Crystal UHD Smart TV',
    category: 'TVs',
    price: 599,
    capacity: 'Large',
    features: '4K Smart TV',
    stock: 'In stock'
  },

  {
    id: 6,
    icon: '▤',
    brand: 'Panasonic',
    name: 'LED Smart TV',
    category: 'TVs',
    price: 399,
    capacity: 'Medium',
    features: 'Full HD',
    stock: 'In stock'
  },

  {
    id: 7,
    icon: '⌂',
    brand: 'Gree',
    name: 'Split Air Conditioner',
    category: 'Kitchen Appliances',
    price: 1099,
    capacity: 'Large',
    features: 'Inverter cooling',
    stock: 'In stock'
  },

  {
    id: 8,
    icon: '⌂',
    brand: 'Panasonic',
    name: 'Microwave Oven',
    category: 'Kitchen Appliances',
    price: 199,
    capacity: 'Small',
    features: 'Digital controls',
    stock: 'In stock'
  }

]


const filteredProducts = computed(() => {

  return products.filter(product => {

    const term = search.value
      .toLowerCase()
      .trim()


    const matchesSearch =
      !term ||
      `${product.name} ${product.brand} ${product.category}`
        .toLowerCase()
        .includes(term)


    const matchesCategory =
      category.value === 'All' ||
      product.category === category.value


    const matchesBrand =
      brand.value === 'All' ||
      product.brand === brand.value


    const matchesCapacity =
      capacity.value === 'All' ||
      product.capacity === capacity.value


    const matchesPrice =
      priceRange.value === 'All' ||
      (
        priceRange.value === 'under500' &&
        product.price < 500
      ) ||
      (
        priceRange.value === '500to1000' &&
        product.price >= 500 &&
        product.price <= 1000
      ) ||
      (
        priceRange.value === 'over1000' &&
        product.price > 1000
      )


    return (
      matchesSearch &&
      matchesCategory &&
      matchesBrand &&
      matchesCapacity &&
      matchesPrice
    )

  })

})


function resetFilters() {

  search.value = ''
  category.value = 'All'
  brand.value = 'All'
  priceRange.value = 'All'
  capacity.value = 'All'

}

</script>