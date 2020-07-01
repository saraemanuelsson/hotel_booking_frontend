<template>
  <form v-on:submit="addBooking">
    <div class="a">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name">
    </div>

    <div class="a">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email">
    </div>

    <div>
        <label for="checked-in">Checked In:</label>
        <input type="checkbox" id="checked-in" v-model="checkedIn">
    </div>

    <div>
        <button type="submit">Send</button>
    </div>
  </form>
</template>

<script>
import { eventBus } from "../main.js"
import BookingsService from "../services/BookingsService.js"


export default {
    name: "booking-form",
    data() {
        return {
            name: "",
            email: "",
            checkedIn: false
        }
    },
    methods: {
        addBooking(e) {
            e.preventDefault()
            const booking = {
                name: this.name,
                email: this.email,
                checkedIn: this.checkedIn
            }
            BookingsService.postBooking(booking)
            .then(res => eventBus.$emit("booking-added", res))
            e.target.reset()
        }
    }
}
</script>

<style>

</style>