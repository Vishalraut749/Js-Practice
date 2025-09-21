<template>
  <section class="py-20 bg-gray-50">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-4">Our Services</h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Choose from our wide range of premium transportation services designed to meet your every need
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="(service, index) in services" :key="index" class="card p-8 text-center">
          <div class="w-16 h-16 bg-gradient-to-r from-primary-500 to-secondary-500 rounded-full flex items-center justify-center mx-auto mb-6">
            <component :is="service.icon" class="w-8 h-8 text-white" />
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">{{ service.title }}</h3>
          <p class="text-gray-600 mb-6 leading-relaxed">{{ service.description }}</p>
          <div class="text-3xl font-bold text-primary-600 mb-4">{{ service.price }}</div>
          <ul class="text-left space-y-2 mb-6">
            <li v-for="feature in service.features" :key="feature" class="flex items-center">
              <svg class="w-5 h-5 text-green-500 mr-2" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/>
              </svg>
              {{ feature }}
            </li>
          </ul>
          <button @click="$emit('book-service', service)" class="btn-primary w-full">
            Book {{ service.title }}
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Services',
  emits: ['book-service'],
  data() {
    return {
      services: [
        {
          title: 'City Rides',
          description: 'Perfect for daily commutes and city travel with comfortable sedans',
          price: '$15/hour',
          icon: 'CarIcon',
          features: [
            'Professional drivers',
            'Clean vehicles',
            'GPS tracking',
            'Online booking'
          ]
        },
        {
          title: 'Airport Transfer',
          description: 'Reliable airport pickup and drop-off services with flight tracking',
          price: '$45/trip',
          icon: 'PlaneIcon',
          features: [
            'Flight tracking',
            'Meet & greet service',
            'Luggage assistance',
            'Fixed pricing'
          ]
        },
        {
          title: 'Premium Luxury',
          description: 'High-end vehicles for special occasions and business travel',
          price: '$35/hour',
          icon: 'StarIcon',
          features: [
            'Luxury vehicles',
            'Chauffeur service',
            'Complimentary water',
            'VIP treatment'
          ]
        },
        {
          title: 'Group Travel',
          description: 'Spacious vans and minibuses for group transportation needs',
          price: '$60/hour',
          icon: 'UsersIcon',
          features: [
            'Up to 12 passengers',
            'Extra luggage space',
            'Group discounts',
            'Event coordination'
          ]
        },
        {
          title: 'Corporate',
          description: 'Professional transportation solutions for business needs',
          price: '$25/hour',
          icon: 'BriefcaseIcon',
          features: [
            'Corporate accounts',
            'Invoice billing',
            'Priority booking',
            'Executive vehicles'
          ]
        },
        {
          title: 'Special Events',
          description: 'Wedding, party, and special occasion transportation',
          price: '$80/event',
          icon: 'HeartIcon',
          features: [
            'Decorated vehicles',
            'Multiple stops',
            'Photo opportunities',
            'Special packages'
          ]
        }
      ]
    }
  },
  components: {
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
    }
  }
}
</script>