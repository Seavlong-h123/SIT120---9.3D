<template>
  <header class="site-header">

    <div class="header-inner">

      <button
        class="brand"
        type="button"
        @click="$emit('navigate', 'home')"
      >

        <img
          src="../assets/logo.jpg"
          alt="Hun Dy Electronics logo"
        />

        <span>Hun Dy Electronics</span>

      </button>

      <nav
        class="main-nav"
        aria-label="Main navigation"
      >

        <button
          type="button"
          :class="{ active: activeView === 'home' }"
          @click="$emit('navigate', 'home')"
        >
          Home
        </button>

        <button
          type="button"
          :class="{ active: activeView === 'products' }"
          @click="$emit('navigate', 'products')"
        >
          Products
        </button>

        <button
          type="button"
          :class="{ active: activeView === 'contact' }"
          @click="$emit('navigate', 'contact')"
        >
          About / Contact
        </button>

      </nav>

    </div>

  </header>
</template>

<script setup>
defineProps({
  activeView: {
    type: String,
    default: 'home'
  }
})

defineEmits(['navigate'])
</script>