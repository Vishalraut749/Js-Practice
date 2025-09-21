<template>
  <section class="py-20 bg-gray-50">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-4">What Our Customers Say</h2>
        <p class="text-xl text-gray-600 max-w-3xl mx-auto">
          Don't just take our word for it - hear from our satisfied customers
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="(testimonial, index) in testimonials" :key="index" class="card p-6">
          <div class="flex items-center mb-4">
            <div v-for="n in 5" :key="n" class="text-yellow-400">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
              </svg>
            </div>
          </div>
          <blockquote class="text-gray-600 mb-6 italic">
            "{{ testimonial.text }}"
          </blockquote>
          <div class="flex items-center">
            <img :src="testimonial.avatar" :alt="testimonial.name" class="w-12 h-12 rounded-full mr-4">
            <div>
              <div class="font-semibold text-gray-900">{{ testimonial.name }}</div>
              <div class="text-sm text-gray-500">{{ testimonial.role }}</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Stats -->
      <div class="mt-20 grid grid-cols-2 lg:grid-cols-4 gap-8 text-center">
        <div v-for="(stat, index) in stats" :key="index">
          <div class="text-4xl font-bold text-primary-600 mb-2">{{ stat.value }}</div>
          <div class="text-gray-600">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Testimonials',
  data() {
    return {
      testimonials: [
        {
          text: "Excellent service! The driver was punctual, professional, and the car was spotless. I'll definitely use TravelCab again.",
          name: "Sarah Johnson",
          role: "Business Executive",
          avatar: "https://images.unsplash.com/photo-1494790108755-2616b612b786?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        },
        {
          text: "Amazing airport transfer service. They tracked my flight and were waiting for me when I arrived. Stress-free travel!",
          name: "Michael Chen",
          role: "Frequent Traveler",
          avatar: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        },
        {
          text: "Used TravelCab for my wedding day. The luxury car was beautiful and the chauffeur made our day even more special!",
          name: "Emily Rodriguez",
          role: "Bride",
          avatar: "https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        },
        {
          text: "Corporate account setup was seamless. Great for our business travel needs with reliable billing and excellent drivers.",
          name: "David Thompson",
          role: "HR Manager",
          avatar: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        },
        {
          text: "Group travel was handled perfectly. The van was spacious and comfortable for our family vacation transfer.",
          name: "Lisa Park",
          role: "Family Traveler",
          avatar: "https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        },
        {
          text: "24/7 availability is a game-changer. Needed a late-night ride and they were there within minutes. Highly recommended!",
          name: "James Wilson",
          role: "Night Shift Worker",
          avatar: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=150&q=80"
        }
      ],
      stats: [
        { value: '50K+', label: 'Happy Customers' },
        { value: '100K+', label: 'Rides Completed' },
        { value: '500+', label: 'Professional Drivers' },
        { value: '4.9★', label: 'Average Rating' }
      ]
    }
  }
}
</script>