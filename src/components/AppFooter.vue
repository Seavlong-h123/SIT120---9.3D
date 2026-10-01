<template>
  <footer class="site-footer">

    <div class="footer-inner">

      <div>

        <h3>Hun Dy Electronics</h3>

        <p>
          Quality household appliances and electronics
          for every home.
        </p>

        <p>
          © 2026 Hun Dy Electronics. All rights reserved.
        </p>

      </div>

      <div>

        <h3>Contact</h3>

        <p>Phone: +855 12 345 678</p>

        <p>Email: info@hundyelectronics.com</p>

        <p>Monday–Saturday, 8:00 AM–6:00 PM</p>

      </div>

      <nav
        class="footer-links"
        aria-label="Footer navigation"
      >

        <h3>Quick Links</h3>

        <button
          type="button"
          @click="$emit('navigate', 'home')"
        >
          Home
        </button>

        <button
          type="button"
          @click="$emit('navigate', 'products')"
        >
          Products
        </button>

        <button
          type="button"
          @click="$emit('navigate', 'contact')"
        >
          Contact
        </button>

      </nav>

    </div>

  </footer>
</template>

<script setup>
defineEmits(['navigate'])
</script>