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

html {
  background: url("assets/background.jpg") no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  font-family: Arial, Helvetica, sans-serif;
  color: white;
}

</style>
