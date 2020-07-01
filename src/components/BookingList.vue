<template>
  <div>
    <Booking v-for="(booking, key) in bookings" :key="key" :booking="booking" />
  </div>
</template>

<script>
import Booking from "./Booking.vue";

export default {
  data() {
    return {
      bookings: []
    };
  },
  components: {
    Booking
  },
  mounted(){
      //this.booking = something;
  }
};
</script>

<style>
</style>
