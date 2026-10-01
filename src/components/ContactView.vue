<template>

  <div class="page">

    <section class="page-banner">

      <span class="eyebrow">
        Visit or contact us
      </span>

      <h1>
        Store Information & Contact
      </h1>

      <p>
        Find our store details or send a product
        enquiry before you visit.
      </p>

    </section>


    <section class="contact-layout">

      <!-- STORE INFORMATION -->

      <div class="store-panel">

        <img
          src="../assets/pic of shop.jpg"
          alt="Hun Dy Electronics store"
          class="store-photo"
        />


        <span class="eyebrow">
          About Hun Dy Electronics
        </span>

        <h2>
          Helping customers find the right appliance.
        </h2>

        <p>
          Hun Dy Electronics provides household
          appliances and electronics including
          refrigerators, washing machines, televisions,
          air conditioners and kitchen appliances.
        </p>


        <div class="store-details">

          <div>
            <strong>
              Address
            </strong>

            <span>
              Hun Dy Electronics, Sihanoukville
            </span>
          </div>


          <div>
            <strong>
              Opening Hours
            </strong>

            <span>
              Monday–Saturday, 8:00 AM–6:00 PM
            </span>
          </div>


          <div>
            <strong>
              Phone Number
            </strong>

            <span>
              +855 10 991
            </span>
          </div>

        </div>


        <div class="button-row">

          <a
            class="btn btn-primary"
            href="tel:+85512345678"
          >
            Call Store
          </a>

          <a
            class="btn btn-outline"
            href="https://maps.app.goo.gl/kicGvidunhqf2Mqc7"
            target="_blank"
            rel="noreferrer"
          >
            Get Directions
          </a>

        </div>


        <div class="map-placeholder">

          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3921.4211113274255!2d103.5220386!3d10.624356699999998!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3107e1c71530dce9%3A0x53d178bb70e9cdf7!2sHun%20Dy%20Electronic!5e0!3m2!1sen!2sau!4v1790820577265!5m2!1sen!2sau" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="strict-origin-when-cross-origin"></iframe>

        </div>

      </div>


      <!-- FORM -->

      <ContactForm
        :form-title="formTitle"
        @submit-form="$emit('submit-form', $event)"
      />

    </section>

  </div>

</template>


<script setup>

import ContactForm from './ContactForm.vue'


defineProps({

  formTitle: {
    type: String,
    default: 'Product Enquiry Form'
  }

})


defineEmits(['submit-form'])

</script>