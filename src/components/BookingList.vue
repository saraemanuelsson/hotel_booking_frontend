<template>
  <div>
    <Booking v-for="(booking, key) in bookings" :key="key" :booking="booking" />
  </div>
</template>

<script>
import Booking from "./Booking.vue";
import BookingsService from "../services/BookingsService.js"
import { eventBus } from "../main.js"

export default {
  data() {
    return {
      bookings: undefined
    };
  },
  components: {
    Booking
  },
  mounted(){
      BookingsService.getBookings()
      .then(data => this.bookings = data);

      eventBus.$on("booking-added", (booking) => {
          this.bookings.push(booking)
      })
  }
};
</script>

<style>
</style>
