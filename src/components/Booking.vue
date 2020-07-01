<template>
  <div class="box">
    <div>
        <label>id:</label>
        <span>{{ booking._id }}</span>
    </div>
    <div>
        <label>Name:</label>
        <span>{{ booking.name }}</span>
    </div>
    <div>
        <label>Email:</label>
        <span>{{ booking.email }}</span>
    </div>
    <div>
        <label>Checked in:</label>
        <span>{{ booking.checkedIn }}</span>
    </div>
    <button name="delete" v-on:click="deleteBooking">Delete</button>
  </div>
</template>

<script>
import BookingsService from "../services/BookingsService"
import { eventBus } from "../main.js"

export default {

    props: ["booking"],
    methods: {
        deleteBooking() {
            BookingsService.deleteBooking(this.booking._id)
            .then(() => eventBus.$emit("booking-deleted", this.booking._id))
        }
    }
};
</script>

<style>
.box {
    border: 1px solid black;
}
</style>
