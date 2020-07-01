<template>
  <div id="app">
    <booking-form/>
    <BookingList/>
  </div>
</template>

<script>
import BookingList from './components/BookingList.vue';
import BookingForm from "./components/BookingForm.vue";

export default {
  name: 'App',
  components: {
    BookingList,
    BookingForm
  }
}
</script>

<style>

</style>
