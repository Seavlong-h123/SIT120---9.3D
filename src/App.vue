<template>
  <div class="app-shell">

    <AppHeader
      :active-view="activeView"
      @navigate="activeView = $event"
    />

    <main class="main-content">

      <HomeView
        v-if="activeView === 'home'"
        @navigate="activeView = $event"
      />

      <ProductsView
        v-else-if="activeView === 'products'"
        @navigate="activeView = $event"
      />

      <ContactView
        v-else
        :form-title="formTitle"
        @submit-form="handleFormSubmit"
      />

      <!-- Parent acknowledgement card -->
      <section
        v-if="acknowledgement"
        class="ack-card"
        aria-live="polite"
      >

        <span class="eyebrow">
          Customer acknowledgement
        </span>

        <h2>
          Thank you, {{ acknowledgement.name }}!
        </h2>

        <p>
          Your product enquiry has been received.
          We will contact you using your preferred method.
        </p>

        <div class="ack-grid">

          <div>
            <strong>Email</strong>
            <span>{{ acknowledgement.email }}</span>
          </div>

          <div>
            <strong>Phone</strong>
            <span>{{ acknowledgement.phone }}</span>
          </div>

          <div>
            <strong>Product</strong>
            <span>{{ acknowledgement.product }}</span>
          </div>

          <div>
            <strong>Budget</strong>
            <span>${{ acknowledgement.budget }}</span>
          </div>

          <div>
            <strong>Contact method</strong>
            <span>{{ acknowledgement.contactMethod }}</span>
          </div>

          <div>
            <strong>Message</strong>
            <span>{{ acknowledgement.message }}</span>
          </div>

        </div>

      </section>

    </main>

    <AppFooter @navigate="activeView = $event" />

  </div>
</template>

<script setup>
import { ref } from 'vue'

import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import HomeView from './components/HomeView.vue'
import ProductsView from './components/ProductsView.vue'
import ContactView from './components/ContactView.vue'

const activeView = ref('home')

const acknowledgement = ref(null)

const formTitle = 'Product Enquiry Form'

function handleFormSubmit(formData) {
  acknowledgement.value = { ...formData }
  activeView.value = 'contact'
}
</script>