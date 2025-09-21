<template>
  <div>
    <Hero @open-booking="openBookingModal" />
    <Services @book-service="openBookingModal" />
    <Features />
    <Testimonials />
    <CTA @open-booking="openBookingModal" />
    <BookingModal 
      :is-open="showBookingModal" 
      @close="closeBookingModal" 
      @booking-submitted="handleBookingSubmitted"
    />
  </div>
</template>

<script>
import Hero from '../components/Hero.vue'
import Services from '../components/Services.vue'
import Features from '../components/Features.vue'
import Testimonials from '../components/Testimonials.vue'
import CTA from '../components/CTA.vue'
import BookingModal from '../components/BookingModal.vue'

export default {
  name: 'Home',
  components: {
    Hero,
    Services,
    Features,
    Testimonials,
    CTA,
    BookingModal
  },
  data() {
    return {
      showBookingModal: false
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
      // Here you would typically send the booking data to your backend
    }
  }
}
</script>