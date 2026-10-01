<template>
  <div class="page">

    <!-- Hero -->
    <section class="hero">

      <div class="hero-copy">

        <span class="eyebrow">
          Hun Dy Electronics
        </span>

        <h1>
          Quality Appliances for Every Home
        </h1>

        <p>
          Discover reliable household appliances and
          electronics at Hun Dy Electronics. Browse
          products, compare your options and contact
          our store for more information.
        </p>

        <div class="button-row">

          <button
            class="btn btn-primary"
            type="button"
            @click="$emit('navigate', 'products')"
          >
            Browse Products
          </button>

          <button
            class="btn btn-outline"
            type="button"
            @click="$emit('navigate', 'contact')"
          >
            Visit Our Store
          </button>

        </div>

      </div>

      <img
        class="store-hero"
        src="../assets/pic of shop.jpg"
        alt="Hun Dy Electronics store"
      />

    </section>


    <!-- Categories -->
    <section class="section-block">

      <div class="section-heading">

        <div>

          <span class="eyebrow">
            Shop
          </span>

          <h2>
            Shop by Category
          </h2>

        </div>

        <p>
          Find appliances for different areas of your home.
        </p>

      </div>


      <div class="category-grid">

        <button
          class="category-card"
          type="button"
          @click="$emit('navigate', 'products')"
        >

          <span class="category-icon">
            ▣
          </span>

          <strong>
            Refrigerators
          </strong>

          <span>
            View products →
          </span>

        </button>


        <button
          class="category-card"
          type="button"
          @click="$emit('navigate', 'products')"
        >

          <span class="category-icon">
            ◫
          </span>

          <strong>
            Washing Machines
          </strong>

          <span>
            View products →
          </span>

        </button>


        <button
          class="category-card"
          type="button"
          @click="$emit('navigate', 'products')"
        >

          <span class="category-icon">
            ▤
          </span>

          <strong>
            Televisions
          </strong>

          <span>
            View products →
          </span>

        </button>


        <button
          class="category-card"
          type="button"
          @click="$emit('navigate', 'products')"
        >

          <span class="category-icon">
            ⌂
          </span>

          <strong>
            Kitchen Appliances
          </strong>

          <span>
            View products →
          </span>

        </button>

      </div>

    </section>


    <!-- Promotions -->
    <section class="section-block tinted">

      <span class="eyebrow sale">
        Promotions
      </span>

      <h2>
        Current Offers
      </h2>

      <div class="promo-grid">

        <article class="promo-card">

          <span class="promo-badge">
            OFFER
          </span>

          <div class="promo-icon">
            %
          </div>

          <h3>
            Appliance Specials
          </h3>

          <p>
            Ask our store about current appliance
            promotions and selected discounts.
          </p>

        </article>


        <article class="promo-card">

          <span class="promo-badge">
            SAVE
          </span>

          <div class="promo-icon">
            $
          </div>

          <h3>
            Value for Your Home
          </h3>

          <p>
            Compare products and find options that
            match your household needs and budget.
          </p>

        </article>


        <article class="promo-card">

          <span class="promo-badge">
            NEW
          </span>

          <div class="promo-icon">
            +
          </div>

          <h3>
            New Products
          </h3>

          <p>
            Contact us to ask about new products and
            current stock availability.
          </p>

        </article>

      </div>

    </section>


    <!-- Why Choose Us -->
    <section class="why-section">

      <div>

        <span class="eyebrow">
          Why Choose Us
        </span>

        <h2>
          Helping customers choose with confidence.
        </h2>

        <p>
          Explore appliances, compare products and
          contact the store before making a visit.
        </p>

      </div>


      <div class="why-grid">

        <article>

          <strong>
            Product Choice
          </strong>

          <p>
            Explore different household appliance
            categories.
          </p>

        </article>


        <article>

          <strong>
            Helpful Service
          </strong>

          <p>
            Contact us with questions about products,
            prices or availability.
          </p>

        </article>


        <article>

          <strong>
            Physical Store
          </strong>

          <p>
            Find store information before visiting.
          </p>

        </article>

      </div>

    </section>

  </div>
</template>


<script setup>

defineEmits(['navigate'])

</script>