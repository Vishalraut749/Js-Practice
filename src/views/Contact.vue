<template>
  <div class="pt-16">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-primary-600 to-secondary-600 py-20">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 class="text-4xl md:text-6xl font-bold text-white mb-6">Contact Us</h1>
        <p class="text-xl text-gray-200 max-w-3xl mx-auto">
          Get in touch with us for bookings, inquiries, or support
        </p>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="py-20 bg-gray-50">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <!-- Contact Form -->
          <div class="bg-white rounded-xl shadow-lg p-8">
            <h2 class="text-3xl font-bold text-gray-900 mb-6">Send us a Message</h2>
            <form @submit.prevent="submitForm" class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">First Name</label>
                  <input 
                    v-model="form.firstName"
                    type="text" 
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    placeholder="Your first name"
                  >
                </div>
                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-2">Last Name</label>
                  <input 
                    v-model="form.lastName"
                    type="text" 
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    placeholder="Your last name"
                  >
                </div>
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                <input 
                  v-model="form.email"
                  type="email" 
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                  placeholder="your.email@example.com"
                >
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 mb-2">Phone</label>
                <input 
                  v-model="form.phone"
                  type="tel" 
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                  placeholder="+1 (555) 123-4567"
                >
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 mb-2">Subject</label>
                <select 
                  v-model="form.subject"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                >
                  <option value="">Select a subject</option>
                  <option value="booking">Booking Inquiry</option>
                  <option value="support">Customer Support</option>
                  <option value="corporate">Corporate Services</option>
                  <option value="feedback">Feedback</option>
                  <option value="other">Other</option>
                </select>
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-700 mb-2">Message</label>
                <textarea 
                  v-model="form.message"
                  rows="5"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                  placeholder="Tell us how we can help you..."
                ></textarea>
              </div>

              <button 
                type="submit"
                :disabled="!isFormValid"
                class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed"
              >
                Send Message
              </button>
            </form>
          </div>

          <!-- Contact Information -->
          <div class="space-y-8">
            <div class="bg-white rounded-xl shadow-lg p-8">
              <h2 class="text-3xl font-bold text-gray-900 mb-6">Get in Touch</h2>
              <div class="space-y-6">
                <div v-for="(contact, index) in contactInfo" :key="index" class="flex items-start space-x-4">
                  <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center flex-shrink-0">
                    <component :is="contact.icon" class="w-6 h-6 text-primary-600" />
                  </div>
                  <div>
                    <h3 class="font-semibold text-gray-900 mb-1">{{ contact.title }}</h3>
                    <p class="text-gray-600">{{ contact.value }}</p>
                    <p v-if="contact.hours" class="text-sm text-gray-500 mt-1">{{ contact.hours }}</p>
                  </div>
                </div>
              </div>
            </div>

            <!-- Emergency Contact -->
            <div class="bg-red-50 border border-red-200 rounded-xl p-6">
              <h3 class="text-lg font-semibold text-red-800 mb-2">Emergency Contact</h3>
              <p class="text-red-600 mb-2">For urgent assistance or emergencies during your ride:</p>
              <p class="text-xl font-bold text-red-800">+1 (555) 911-HELP</p>
              <p class="text-sm text-red-600 mt-1">Available 24/7</p>
            </div>

            <!-- Office Hours -->
            <div class="bg-white rounded-xl shadow-lg p-8">
              <h3 class="text-xl font-bold text-gray-900 mb-4">Office Hours</h3>
              <div class="space-y-2">
                <div v-for="(hours, day) in officeHours" :key="day" class="flex justify-between">
                  <span class="text-gray-600">{{ day }}</span>
                  <span class="font-medium text-gray-900">{{ hours }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Map Section -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Visit Our Office</h2>
          <p class="text-xl text-gray-600">Find us at our headquarters in the heart of the city</p>
        </div>

        <!-- Placeholder for map -->
        <div class="bg-gray-200 rounded-xl h-96 flex items-center justify-center">
          <div class="text-center">
            <svg class="w-16 h-16 text-gray-400 mx-auto mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
            </svg>
            <p class="text-gray-500">Interactive Map Coming Soon</p>
            <p class="text-sm text-gray-400 mt-2">123 Business District, New York, NY 10001</p>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section class="py-20 bg-gray-50">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Frequently Asked Questions</h2>
          <p class="text-xl text-gray-600">Quick answers to common questions</p>
        </div>

        <div class="max-w-3xl mx-auto space-y-4">
          <div v-for="(faq, index) in faqs" :key="index" class="bg-white rounded-lg shadow-md">
            <button 
              @click="toggleFAQ(index)"
              class="w-full px-6 py-4 text-left flex justify-between items-center focus:outline-none"
            >
              <span class="font-semibold text-gray-900">{{ faq.question }}</span>
              <svg 
                :class="{ 'transform rotate-180': faq.open }"
                class="w-5 h-5 text-gray-500 transition-transform"
                fill="none" 
                stroke="currentColor" 
                viewBox="0 0 24 24"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
              </svg>
            </button>
            <div v-show="faq.open" class="px-6 pb-4">
              <p class="text-gray-600">{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      form: {
        firstName: '',
        lastName: '',
        email: '',
        phone: '',
        subject: '',
        message: ''
      },
      contactInfo: [
        {
          title: 'Phone',
          value: '+1 (555) 123-4567',
          hours: '24/7 Booking & Support',
          icon: 'PhoneIcon'
        },
        {
          title: 'Email',
          value: 'info@travelcab.com',
          hours: 'Response within 2 hours',
          icon: 'MailIcon'
        },
        {
          title: 'Address',
          value: '123 Business District, New York, NY 10001',
          hours: 'Mon-Fri: 9AM-6PM',
          icon: 'LocationIcon'
        }
      ],
      officeHours: {
        'Monday': '9:00 AM - 6:00 PM',
        'Tuesday': '9:00 AM - 6:00 PM',
        'Wednesday': '9:00 AM - 6:00 PM',
        'Thursday': '9:00 AM - 6:00 PM',
        'Friday': '9:00 AM - 6:00 PM',
        'Saturday': '10:00 AM - 4:00 PM',
        'Sunday': 'Closed'
      },
      faqs: [
        {
          question: 'How do I book a ride?',
          answer: 'You can book a ride through our website, mobile app, or by calling us directly at +1 (555) 123-4567. Online booking is available 24/7.',
          open: false
        },
        {
          question: 'What payment methods do you accept?',
          answer: 'We accept cash, all major credit cards (Visa, MasterCard, American Express), and digital payments through our app.',
          open: false
        },
        {
          question: 'Can I cancel or modify my booking?',
          answer: 'Yes, you can cancel or modify your booking up to 30 minutes before the scheduled pickup time without any charges.',
          open: false
        },
        {
          question: 'Are your drivers licensed and insured?',
          answer: 'All our drivers are fully licensed, insured, and undergo comprehensive background checks. Our vehicles are also fully insured and regularly maintained.',
          open: false
        },
        {
          question: 'Do you offer corporate accounts?',
          answer: 'Yes, we offer corporate accounts with special rates, monthly billing, and dedicated account management for businesses.',
          open: false
        }
      ]
    }
  },
  computed: {
    isFormValid() {
      return this.form.firstName && 
             this.form.lastName && 
             this.form.email && 
             this.form.subject && 
             this.form.message
    }
  },
  methods: {
    submitForm() {
      if (this.isFormValid) {
        console.log('Form submitted:', this.form)
        alert('Thank you for your message! We will get back to you within 24 hours.')
        this.resetForm()
      }
    },
    resetForm() {
      this.form = {
        firstName: '',
        lastName: '',
        email: '',
        phone: '',
        subject: '',
        message: ''
      }
    },
    toggleFAQ(index) {
      this.faqs[index].open = !this.faqs[index].open
    }
  },
  components: {
    PhoneIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>`
    },
    MailIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>`
    },
    LocationIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>`
    }
  }
}
</script>