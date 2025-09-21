<template>
  <div class="pt-16">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-primary-600 to-secondary-600 py-20">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 class="text-4xl md:text-6xl font-bold text-white mb-6">Our Services</h1>
        <p class="text-xl text-gray-200 max-w-3xl mx-auto">
          Comprehensive transportation solutions for every occasion and need
        </p>
      </div>
    </section>

    <!-- Services Grid -->
    <section class="py-20 bg-gray-50">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 mb-16">
          <div v-for="(service, index) in detailedServices" :key="index" class="card p-8">
            <div class="flex items-start space-x-6">
              <div class="w-16 h-16 bg-gradient-to-r from-primary-500 to-secondary-500 rounded-xl flex items-center justify-center flex-shrink-0">
                <component :is="service.icon" class="w-8 h-8 text-white" />
              </div>
              <div class="flex-1">
                <h3 class="text-2xl font-bold text-gray-900 mb-3">{{ service.title }}</h3>
                <p class="text-gray-600 mb-4 leading-relaxed">{{ service.description }}</p>
                <div class="text-2xl font-bold text-primary-600 mb-4">{{ service.price }}</div>
                
                <div class="mb-6">
                  <h4 class="font-semibold text-gray-900 mb-2">Features:</h4>
                  <ul class="space-y-1">
                    <li v-for="feature in service.features" :key="feature" class="flex items-center text-sm text-gray-600">
                      <svg class="w-4 h-4 text-green-500 mr-2" fill="currentColor" viewBox="0 0 20 20">
                        <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/>
                      </svg>
                      {{ feature }}
                    </li>
                  </ul>
                </div>

                <button @click="openBookingModal" class="btn-primary w-full">
                  Book {{ service.title }}
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- Additional Info -->
        <div class="bg-white rounded-xl shadow-lg p-8">
          <h2 class="text-3xl font-bold text-gray-900 mb-6 text-center">Why Choose Our Services?</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            <div v-for="(benefit, index) in benefits" :key="index" class="text-center">
              <div class="w-12 h-12 bg-primary-100 rounded-lg flex items-center justify-center mx-auto mb-3">
                <component :is="benefit.icon" class="w-6 h-6 text-primary-600" />
              </div>
              <h3 class="font-semibold text-gray-900 mb-2">{{ benefit.title }}</h3>
              <p class="text-sm text-gray-600">{{ benefit.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <BookingModal 
      :is-open="showBookingModal" 
      @close="closeBookingModal" 
      @booking-submitted="handleBookingSubmitted"
    />
  </div>
</template>

<script>
import BookingModal from '../components/BookingModal.vue'

export default {
  name: 'Services',
  components: {
    BookingModal
  },
  data() {
    return {
      showBookingModal: false,
      detailedServices: [
        {
          title: 'City Rides',
          description: 'Perfect for daily commutes, shopping trips, and city exploration. Our comfortable sedans provide reliable transportation throughout the city.',
          price: '$15/hour',
          icon: 'CarIcon',
          features: [
            'Professional drivers with local knowledge',
            'Clean and well-maintained vehicles',
            'Real-time GPS tracking',
            'Flexible pickup and drop-off locations',
            'Online booking and payment',
            'Competitive hourly rates'
          ]
        },
        {
          title: 'Airport Transfer',
          description: 'Stress-free airport transportation with flight tracking, meet & greet service, and professional assistance with your luggage.',
          price: '$45/trip',
          icon: 'PlaneIcon',
          features: [
            'Flight tracking and monitoring',
            'Meet & greet service at arrivals',
            'Professional luggage assistance',
            'Fixed pricing - no surge charges',
            'Spacious vehicles for luggage',
            'Complimentary waiting time'
          ]
        },
        {
          title: 'Premium Luxury',
          description: 'Experience the ultimate in comfort and style with our luxury fleet. Perfect for special occasions and executive travel.',
          price: '$35/hour',
          icon: 'StarIcon',
          features: [
            'High-end luxury vehicles (BMW, Mercedes, Audi)',
            'Professional chauffeur service',
            'Complimentary bottled water and mints',
            'VIP treatment and white-glove service',
            'Executive amenities and Wi-Fi',
            'Red carpet service for special events'
          ]
        },
        {
          title: 'Group Travel',
          description: 'Spacious vans and minibuses perfect for family trips, corporate outings, and group transportation needs.',
          price: '$60/hour',
          icon: 'UsersIcon',
          features: [
            'Vehicles accommodating 8-12 passengers',
            'Extra luggage and equipment space',
            'Group booking discounts available',
            'Event coordination and planning assistance',
            'Multiple pickup and drop-off locations',
            'Professional group travel management'
          ]
        },
        {
          title: 'Corporate Solutions',
          description: 'Comprehensive business transportation solutions with corporate accounts, priority booking, and executive service.',
          price: '$25/hour',
          icon: 'BriefcaseIcon',
          features: [
            'Dedicated corporate account management',
            'Monthly invoice billing and reporting',
            'Priority booking and dispatch',
            'Executive vehicle fleet',
            'Airport and hotel partnerships',
            'Custom transportation solutions'
          ]
        },
        {
          title: 'Special Events',
          description: 'Make your special day memorable with our event transportation services including weddings, parties, and celebrations.',
          price: '$80/event',
          icon: 'HeartIcon',
          features: [
            'Decorated vehicles for special occasions',
            'Multiple ceremony and reception stops',
            'Professional event photography opportunities',
            'Customizable special event packages',
            'Coordination with wedding planners',
            'Backup vehicles and contingency planning'
          ]
        }
      ],
      benefits: [
        {
          title: 'Licensed & Insured',
          description: 'All drivers and vehicles are fully licensed and insured',
          icon: 'ShieldIcon'
        },
        {
          title: 'Transparent Pricing',
          description: 'No hidden fees or surprise charges',
          icon: 'DollarIcon'
        },
        {
          title: 'Real-time Updates',
          description: 'Live tracking and status updates',
          icon: 'ClockIcon'
        },
        {
          title: 'Customer Support',
          description: '24/7 customer service and assistance',
          icon: 'PhoneIcon'
        }
      ]
    }
  },
  methods: {
    openBookingModal() {
      this.showBookingModal = true
    },
    closeBookingModal() {
      this.showBookingModal = false
    },
    handleBookingSubmitted(bookingData) {
      console.log('Booking submitted:', bookingData)
    }
  },
  components: {
    BookingModal,
    CarIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path d="M8 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM15 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z"/><path d="M3 4a1 1 0 00-1 1v10a1 1 0 001 1h1.05a2.5 2.5 0 014.9 0H10a1 1 0 001-1V5a1 1 0 00-1-1H3zM14 7a1 1 0 00-1 1v6.05A2.5 2.5 0 0115.95 16H17a1 1 0 001-1V8a1 1 0 00-1-1h-3z"/></svg>`
    },
    PlaneIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/></svg>`
    },
    StarIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>`
    },
    UsersIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path d="M9 6a3 3 0 11-6 0 3 3 0 016 0zM17 6a3 3 0 11-6 0 3 3 0 016 0zM12.93 17c.046-.327.07-.66.07-1a6.97 6.97 0 00-1.5-4.33A5 5 0 0119 16v1h-6.07zM6 11a5 5 0 015 5v1H1v-1a5 5 0 015-5z"/></svg>`
    },
    BriefcaseIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M6 6V5a3 3 0 013-3h2a3 3 0 013 3v1h2a2 2 0 012 2v6a2 2 0 01-2 2H4a2 2 0 01-2-2V8a2 2 0 012-2h2zm4-3a1 1 0 00-1 1v1h2V4a1 1 0 00-1-1z" clip-rule="evenodd"/></svg>`
    },
    HeartIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M3.172 5.172a4 4 0 015.656 0L10 6.343l1.172-1.171a4 4 0 115.656 5.656L10 17.657l-6.828-6.829a4 4 0 010-5.656z" clip-rule="evenodd"/></svg>`
    },
    ShieldIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>`
    },
    DollarIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1"/></svg>`
    },
    ClockIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`
    },
    PhoneIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>`
    }
  }
}
</script>