<template>
  <section class="hero-bg min-h-screen flex items-center justify-center relative overflow-hidden">
    <!-- Background Animation -->
    <div class="absolute inset-0">
      <div class="absolute top-20 left-10 w-20 h-20 bg-white bg-opacity-10 rounded-full animate-bounce-slow"></div>
      <div class="absolute top-40 right-20 w-16 h-16 bg-white bg-opacity-10 rounded-full animate-bounce-slow" style="animation-delay: 1s;"></div>
      <div class="absolute bottom-40 left-20 w-12 h-12 bg-white bg-opacity-10 rounded-full animate-bounce-slow" style="animation-delay: 2s;"></div>
    </div>

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10">
      <div class="animate-fade-in">
        <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold text-white mb-6 leading-tight">
          Premium <span class="text-yellow-400">Cab Service</span><br>
          <span class="text-3xl md:text-5xl lg:text-6xl">Wherever You Go</span>
        </h1>
        <p class="text-xl md:text-2xl text-gray-200 mb-8 max-w-3xl mx-auto leading-relaxed">
          Experience luxury, safety, and reliability with our professional drivers and premium vehicles. 
          Available 24/7 for all your travel needs.
        </p>
        
        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mb-12">
          <button @click="$emit('open-booking')" class="btn-primary text-lg px-8 py-4 animate-slide-up">
            <svg class="w-5 h-5 mr-2 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3a2 2 0 012-2h4a2 2 0 012 2v4m-6 0V6a2 2 0 012-2h4a2 2 0 012 2v1M8 7h8m-8 0l-2 9a2 2 0 002 2h8a2 2 0 002-2l-2-9"/>
            </svg>
            Book Your Ride
          </button>
          <button class="btn-secondary text-lg px-8 py-4 animate-slide-up" style="animation-delay: 0.2s;">
            <svg class="w-5 h-5 mr-2 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
            </svg>
            Call Now
          </button>
        </div>

        <!-- Features -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 max-w-4xl mx-auto">
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-lg p-6 animate-slide-up" style="animation-delay: 0.4s;">
            <div class="w-12 h-12 bg-yellow-400 rounded-lg flex items-center justify-center mx-auto mb-4">
              <svg class="w-6 h-6 text-gray-900" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/>
              </svg>
            </div>
            <h3 class="text-lg font-semibold text-white mb-2">24/7 Available</h3>
            <p class="text-gray-300">Round the clock service for all your travel needs</p>
          </div>
          
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-lg p-6 animate-slide-up" style="animation-delay: 0.6s;">
            <div class="w-12 h-12 bg-yellow-400 rounded-lg flex items-center justify-center mx-auto mb-4">
              <svg class="w-6 h-6 text-gray-900" fill="currentColor" viewBox="0 0 20 20">
                <path d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
              </svg>
            </div>
            <h3 class="text-lg font-semibold text-white mb-2">Safe & Secure</h3>
            <p class="text-gray-300">Professional drivers with verified backgrounds</p>
          </div>
          
          <div class="bg-white bg-opacity-10 backdrop-blur-sm rounded-lg p-6 animate-slide-up" style="animation-delay: 0.8s;">
            <div class="w-12 h-12 bg-yellow-400 rounded-lg flex items-center justify-center mx-auto mb-4">
              <svg class="w-6 h-6 text-gray-900" fill="currentColor" viewBox="0 0 20 20">
                <path d="M3 4a1 1 0 011-1h12a1 1 0 011 1v2a1 1 0 01-1 1H4a1 1 0 01-1-1V4zM3 10a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H4a1 1 0 01-1-1v-6zM14 9a1 1 0 00-1 1v6a1 1 0 001 1h2a1 1 0 001-1v-6a1 1 0 00-1-1h-2z"/>
              </svg>
            </div>
            <h3 class="text-lg font-semibold text-white mb-2">Best Prices</h3>
            <p class="text-gray-300">Competitive rates with transparent pricing</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
      <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
      </svg>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  emits: ['open-booking']
}
</script>