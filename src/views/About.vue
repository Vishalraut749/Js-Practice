<template>
  <div class="pt-16">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-primary-600 to-secondary-600 py-20">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h1 class="text-4xl md:text-6xl font-bold text-white mb-6">About TravelCab</h1>
        <p class="text-xl text-gray-200 max-w-3xl mx-auto">
          Your trusted partner in premium transportation services since 2015
        </p>
      </div>
    </section>

    <!-- Story Section -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <div>
            <h2 class="text-4xl font-bold text-gray-900 mb-6">Our Story</h2>
            <p class="text-gray-600 mb-6 leading-relaxed">
              Founded in 2015, TravelCab began with a simple mission: to provide safe, reliable, and comfortable transportation services that exceed customer expectations. What started as a small fleet of three vehicles has grown into a comprehensive transportation solution serving thousands of customers across the city.
            </p>
            <p class="text-gray-600 mb-6 leading-relaxed">
              Our commitment to excellence, safety, and customer satisfaction has made us the preferred choice for individuals, families, and businesses seeking premium transportation services. We've built our reputation on trust, reliability, and going the extra mile for every passenger.
            </p>
            <p class="text-gray-600 leading-relaxed">
              Today, we operate a modern fleet of over 100 vehicles, employ more than 500 professional drivers, and have completed over 100,000 successful rides. But our core values remain the same: putting our customers first and delivering exceptional service every time.
            </p>
          </div>
          <div class="relative">
            <img 
              src="https://images.unsplash.com/photo-1449824913935-59a10b8d2000?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" 
              alt="TravelCab fleet" 
              class="rounded-lg shadow-xl"
            >
            <div class="absolute -bottom-6 -right-6 bg-primary-600 text-white p-6 rounded-lg shadow-lg">
              <div class="text-3xl font-bold">9+</div>
              <div class="text-sm">Years of Service</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Values Section -->
    <section class="py-20 bg-gray-50">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Our Values</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            The principles that guide everything we do
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(value, index) in values" :key="index" class="card p-8 text-center">
            <div class="w-16 h-16 bg-gradient-to-r from-primary-500 to-secondary-500 rounded-full flex items-center justify-center mx-auto mb-6">
              <component :is="value.icon" class="w-8 h-8 text-white" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-4">{{ value.title }}</h3>
            <p class="text-gray-600 leading-relaxed">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Meet Our Leadership</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            The experienced professionals leading TravelCab into the future
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="(member, index) in team" :key="index" class="card p-6 text-center">
            <img :src="member.photo" :alt="member.name" class="w-24 h-24 rounded-full mx-auto mb-4 object-cover">
            <h3 class="text-xl font-bold text-gray-900 mb-2">{{ member.name }}</h3>
            <p class="text-primary-600 font-medium mb-3">{{ member.role }}</p>
            <p class="text-gray-600 text-sm leading-relaxed">{{ member.bio }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="py-20 bg-gradient-to-r from-primary-600 to-secondary-600">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-white mb-4">TravelCab by the Numbers</h2>
          <p class="text-xl text-gray-200">Our achievements and milestones</p>
        </div>

        <div class="grid grid-cols-2 lg:grid-cols-4 gap-8 text-center">
          <div v-for="(stat, index) in stats" :key="index" class="bg-white bg-opacity-10 backdrop-blur-sm rounded-lg p-6">
            <div class="text-4xl font-bold text-white mb-2">{{ stat.value }}</div>
            <div class="text-gray-200">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      values: [
        {
          title: 'Safety First',
          description: 'Every vehicle is regularly inspected and maintained. All drivers undergo thorough background checks and safety training.',
          icon: 'ShieldIcon'
        },
        {
          title: 'Customer Excellence',
          description: 'We go above and beyond to ensure every customer has an exceptional experience from booking to destination.',
          icon: 'StarIcon'
        },
        {
          title: 'Reliability',
          description: 'On-time service you can count on. We understand the importance of punctuality in your daily schedule.',
          icon: 'ClockIcon'
        },
        {
          title: 'Innovation',
          description: 'Continuously improving our services with the latest technology for booking, tracking, and customer communication.',
          icon: 'LightbulbIcon'
        },
        {
          title: 'Integrity',
          description: 'Transparent pricing, honest communication, and ethical business practices in all our interactions.',
          icon: 'HeartIcon'
        },
        {
          title: 'Community',
          description: 'Proud to serve our local community and contribute to the economic growth of our city.',
          icon: 'UsersIcon'
        }
      ],
      team: [
        {
          name: 'John Anderson',
          role: 'CEO & Founder',
          bio: 'With over 15 years in the transportation industry, John founded TravelCab with a vision to revolutionize urban mobility.',
          photo: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80'
        },
        {
          name: 'Sarah Mitchell',
          role: 'Operations Director',
          bio: 'Sarah oversees our daily operations, ensuring every ride meets our high standards of quality and service.',
          photo: 'https://images.unsplash.com/photo-1494790108755-2616b612b786?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80'
        },
        {
          name: 'Michael Chen',
          role: 'Technology Lead',
          bio: 'Michael leads our technology initiatives, developing innovative solutions to enhance customer experience.',
          photo: 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80'
        }
      ],
      stats: [
        { value: '100K+', label: 'Rides Completed' },
        { value: '50K+', label: 'Happy Customers' },
        { value: '500+', label: 'Professional Drivers' },
        { value: '100+', label: 'Fleet Vehicles' }
      ]
    }
  },
  components: {
    ShieldIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/></svg>`
    },
    StarIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>`
    },
    ClockIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`
    },
    LightbulbIcon: {
      template: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/></svg>`
    },
    HeartIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M3.172 5.172a4 4 0 015.656 0L10 6.343l1.172-1.171a4 4 0 115.656 5.656L10 17.657l-6.828-6.829a4 4 0 010-5.656z" clip-rule="evenodd"/></svg>`
    },
    UsersIcon: {
      template: `<svg fill="currentColor" viewBox="0 0 20 20"><path d="M9 6a3 3 0 11-6 0 3 3 0 016 0zM17 6a3 3 0 11-6 0 3 3 0 016 0zM12.93 17c.046-.327.07-.66.07-1a6.97 6.97 0 00-1.5-4.33A5 5 0 0119 16v1h-6.07zM6 11a5 5 0 015 5v1H1v-1a5 5 0 015-5z"/></svg>`
    }
  }
}
</script>