<template>
  <div>
    <Booking v-for="(booking, key) in bookings" :key="key" :booking="booking" />
  </div>
</template>

<script>
import Booking from "./Booking.vue";
import BookingsService from "../services/BookingsService.js"

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
  }
};
</script>

<style>
</style>
