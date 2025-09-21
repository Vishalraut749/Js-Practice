<template>
  <div v-if="isOpen" class="fixed inset-0 z-50 overflow-y-auto" @click="closeModal">
    <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
      <!-- Background overlay -->
      <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>

      <!-- Modal panel -->
      <div 
        class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
        @click.stop
      >
        <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
          <div class="sm:flex sm:items-start">
            <div class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-primary-100 sm:mx-0 sm:h-10 sm:w-10">
              <svg class="h-6 w-6 text-primary-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3a2 2 0 012-2h4a2 2 0 012 2v4m-6 0V6a2 2 0 012-2h4a2 2 0 012 2v1M8 7h8m-8 0l-2 9a2 2 0 002 2h8a2 2 0 002-2l-2-9"/>
              </svg>
            </div>
            <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left w-full">
              <h3 class="text-lg leading-6 font-medium text-gray-900 mb-4">
                Book Your Ride
              </h3>
              
              <form @submit.prevent="submitBooking" class="space-y-4">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Pickup Location</label>
                    <input 
                      v-model="booking.pickupLocation"
                      type="text" 
                      required
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                      placeholder="Enter pickup address"
                    >
                  </div>
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Destination</label>
                    <input 
                      v-model="booking.destination"
                      type="text" 
                      required
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                      placeholder="Enter destination"
                    >
                  </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Date</label>
                    <input 
                      v-model="booking.date"
                      type="date" 
                      required
                      :min="today"
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    >
                  </div>
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Time</label>
                    <input 
                      v-model="booking.time"
                      type="time" 
                      required
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    >
                  </div>
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-1">Service Type</label>
                  <select 
                    v-model="booking.serviceType"
                    required
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                  >
                    <option value="">Select service type</option>
                    <option value="city-rides">City Rides - $15/hour</option>
                    <option value="airport-transfer">Airport Transfer - $45/trip</option>
                    <option value="premium-luxury">Premium Luxury - $35/hour</option>
                    <option value="group-travel">Group Travel - $60/hour</option>
                    <option value="corporate">Corporate - $25/hour</option>
                    <option value="special-events">Special Events - $80/event</option>
                  </select>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Passengers</label>
                    <select 
                      v-model="booking.passengers"
                      required
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    >
                      <option value="">Select passengers</option>
                      <option v-for="n in 8" :key="n" :value="n">{{ n }} {{ n === 1 ? 'Passenger' : 'Passengers' }}</option>
                    </select>
                  </div>
                  <div>
                    <label class="block text-sm font-medium text-gray-700 mb-1">Phone</label>
                    <input 
                      v-model="booking.phone"
                      type="tel" 
                      required
                      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                      placeholder="Your phone number"
                    >
                  </div>
                </div>

                <div>
                  <label class="block text-sm font-medium text-gray-700 mb-1">Special Requirements (Optional)</label>
                  <textarea 
                    v-model="booking.notes"
                    rows="3"
                    class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500"
                    placeholder="Any special requirements or notes..."
                  ></textarea>
                </div>

                <div class="bg-gray-50 p-4 rounded-lg">
                  <div class="flex justify-between items-center">
                    <span class="text-sm font-medium text-gray-700">Estimated Cost:</span>
                    <span class="text-lg font-bold text-primary-600">{{ estimatedCost }}</span>
                  </div>
                </div>
              </form>
            </div>
          </div>
        </div>
        
        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
          <button 
            @click="submitBooking"
            :disabled="!isFormValid"
            class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-primary-600 text-base font-medium text-white hover:bg-primary-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary-500 sm:ml-3 sm:w-auto sm:text-sm disabled:opacity-50 disabled:cursor-not-allowed transition-colors duration-200"
          >
            Book Now
          </button>
          <button 
            @click="closeModal"
            class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm transition-colors duration-200"
          >
            Cancel
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BookingModal',
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  emits: ['close', 'booking-submitted'],
  data() {
    return {
      booking: {
        pickupLocation: '',
        destination: '',
        date: '',
        time: '',
        serviceType: '',
        passengers: '',
        phone: '',
        notes: ''
      }
    }
  },
  computed: {
    today() {
      return new Date().toISOString().split('T')[0]
    },
    isFormValid() {
      return this.booking.pickupLocation && 
             this.booking.destination && 
             this.booking.date && 
             this.booking.time && 
             this.booking.serviceType && 
             this.booking.passengers && 
             this.booking.phone
    },
    estimatedCost() {
      const prices = {
        'city-rides': '$15-30',
        'airport-transfer': '$45-60',
        'premium-luxury': '$35-50',
        'group-travel': '$60-90',
        'corporate': '$25-40',
        'special-events': '$80-120'
      }
      return prices[this.booking.serviceType] || 'Select service'
    }
  },
  methods: {
    closeModal() {
      this.$emit('close')
      this.resetForm()
    },
    resetForm() {
      this.booking = {
        pickupLocation: '',
        destination: '',
        date: '',
        time: '',
        serviceType: '',
        passengers: '',
        phone: '',
        notes: ''
      }
    },
    submitBooking() {
      if (this.isFormValid) {
        this.$emit('booking-submitted', { ...this.booking })
        this.closeModal()
        // Show success message
        alert('Booking submitted successfully! We will contact you shortly to confirm your ride.')
      }
    }
  },
  mounted() {
    // Set default date to today
    this.booking.date = this.today
    // Set default time to current time + 1 hour
    const now = new Date()
    now.setHours(now.getHours() + 1)
    this.booking.time = now.toTimeString().slice(0, 5)
  }
}
</script>