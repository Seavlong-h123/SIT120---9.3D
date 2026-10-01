<template>
  <section class="form-panel">

    <span class="eyebrow">
      Ask us a question
    </span>

    <h2>
      {{ formTitle }}
    </h2>

    <p>
      Ask about product availability, price,
      delivery or other product information.
    </p>

    <form
      @submit.prevent="handleSubmit"
      novalidate
    >

      <div class="form-grid">

        <!-- Full Name -->
        <label>
          Full Name <span>*</span>

          <input
            v-model="form.name"
            type="text"
            placeholder="Your name"
          />

          <small
            v-if="errors.name"
            class="error"
          >
            {{ errors.name }}
          </small>
        </label>


        <!-- Email -->
        <label>
          Email <span>*</span>

          <input
            v-model="form.email"
            type="email"
            placeholder="you@example.com"
          />

          <small
            v-if="errors.email"
            class="error"
          >
            {{ errors.email }}
          </small>
        </label>


        <!-- Phone -->
        <label>
          Phone Number <span>*</span>

          <input
            v-model="form.phone"
            type="tel"
            placeholder="Your phone number"
          />

          <small
            v-if="errors.phone"
            class="error"
          >
            {{ errors.phone }}
          </small>
        </label>


        <!-- Number input -->
        <label>
          Estimated Budget ($) <span>*</span>

          <input
            v-model.number="form.budget"
            type="number"
            min="1"
            placeholder="500"
          />

          <small
            v-if="errors.budget"
            class="error"
          >
            {{ errors.budget }}
          </small>
        </label>


        <!-- Dropdown with v-for -->
        <label>
          Product Category <span>*</span>

          <select v-model="form.product">

            <option value="">
              Choose a category
            </option>

            <option
              v-for="option in productOptions"
              :key="option"
              :value="option"
            >
              {{ option }}
            </option>

          </select>

          <small
            v-if="errors.product"
            class="error"
          >
            {{ errors.product }}
          </small>
        </label>

      </div>


      <!-- Radio buttons -->
      <fieldset>

        <legend>
          Preferred Contact Method <span>*</span>
        </legend>

        <div class="radio-row">

          <label
            v-for="method in contactMethods"
            :key="method"
            class="radio-label"
          >

            <input
              v-model="form.contactMethod"
              type="radio"
              name="contactMethod"
              :value="method"
            />

            {{ method }}

          </label>

        </div>

        <small
          v-if="errors.contactMethod"
          class="error"
        >
          {{ errors.contactMethod }}
        </small>

      </fieldset>


      <!-- Message -->
      <label>
        Message <span>*</span>

        <textarea
          v-model="form.message"
          rows="5"
          maxlength="500"
          placeholder="Tell us what you would like to know..."
        ></textarea>

        <small class="character-count">
          {{ form.message.length }}/500
        </small>

        <small
          v-if="errors.message"
          class="error"
        >
          {{ errors.message }}
        </small>
      </label>


      <!-- Checkbox -->
      <label class="check-label">

        <input
          v-model="form.updates"
          type="checkbox"
        />

        Send me occasional updates about
        promotions and new products.

      </label>


      <button
         class="btn btn-primary submit-btn"
         type="submit"
      >
        Send Enquiry
      </button>

      <p
        v-if="showResetMessage"
        class="reset-message"
      >
        ✓ Your enquiry has been submitted. The form will reset in 2 seconds.
      </p>

      <p class="required-note">
      * Required fields
      </p>

    </form>

  </section>
</template>


<script setup>

import { reactive, ref } from 'vue'


/* PROPS */
defineProps({
  formTitle: {
    type: String,
    default: 'Product Enquiry Form'
  }
})


/* EMIT */
const emit = defineEmits([
  'submit-form'
])
const showResetMessage = ref(false)


/* Dropdown options */
const productOptions = [
  'Refrigerators',
  'Washing Machines',
  'Televisions',
  'Air Conditioners',
  'Kitchen Appliances'
]


/* Radio options */
const contactMethods = [
  'Email',
  'Phone'
]


/* Form data */
const form = reactive({
  name: '',
  email: '',
  phone: '',
  budget: null,
  product: '',
  contactMethod: '',
  message: '',
  updates: false
})


/* Validation errors */
const errors = reactive({
  name: '',
  email: '',
  phone: '',
  budget: '',
  product: '',
  contactMethod: '',
  message: ''
})


/* Validate form */
function validate() {

  Object.keys(errors).forEach(key => {
    errors[key] = ''
  })

  let valid = true


  if (!form.name.trim()) {
    errors.name = 'Please enter your name.'
    valid = false
  }


  if (!form.email.trim()) {

    errors.email = 'Please enter your email.'
    valid = false

  } else if (
    !/^\S+@\S+\.\S+$/.test(form.email)
  ) {

    errors.email =
      'Please enter a valid email address.'

    valid = false
  }


  if (!form.phone.trim()) {
    errors.phone = 'Please enter your phone number.'
    valid = false
  }


  if (!form.budget || form.budget <= 0) {
    errors.budget =
      'Please enter a budget greater than 0.'
    valid = false
  }


  if (!form.product) {
    errors.product =
      'Please choose a product category.'
    valid = false
  }


  if (!form.contactMethod) {
    errors.contactMethod =
      'Please choose a contact method.'
    valid = false
  }


  if (!form.message.trim()) {
    errors.message =
      'Please enter a message.'
    valid = false
  }


  return valid
}


/* Reset form */
function resetForm() {

  form.name = ''
  form.email = ''
  form.phone = ''
  form.budget = null
  form.product = ''
  form.contactMethod = ''
  form.message = ''
  form.updates = false

}


/* Submit form */
function handleSubmit() {

  if (!validate()) {
    return
  }

  emit('submit-form', {
    ...form
  })

  showResetMessage.value = true

  setTimeout(() => {
    resetForm()
    showResetMessage.value = false
  }, 2000)

}

</script>