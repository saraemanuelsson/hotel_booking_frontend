<template>
  <div class="box">
    <div>
        <label>Name:</label>
        <EditableText :value="booking.name" v-on:edited="editedName"/>
    </div>
    <div>
        <label>Email:</label>
        <EditableText :value="booking.email" v-on:edited="editedEmail"/>
    </div>
    <div>
        <label for="checkbox">Checked In:</label>
        <input type="checkbox" v-model="booking.checkedIn" v-on:change="updateBooking" id="checkbox">
    </div>
    <button name="delete" v-on:click="deleteBooking">Delete</button>
  </div>
</template>

<script>
import BookingsService from "../services/BookingsService"
import EditableText from "./EditableText"
import { eventBus } from "../main.js"

export default {
    props: ["booking"],
    methods: {
        deleteBooking() {
            BookingsService.deleteBooking(this.booking._id)
            .then(() => eventBus.$emit("booking-deleted", this.booking._id))
        },
        updateBooking() {
            const bookingWithoutId = {
                name: this.booking.name,
                email: this.booking.email,
                checkedIn: this.booking.checkedIn
            };
            BookingsService.updateBooking(this.booking._id, bookingWithoutId);
        },
        editedName(newName) {
            this.booking.name = newName
            this.updateBooking()
        },
        editedEmail(newEmail) {
            this.booking.email = newEmail
            this.updateBooking()
        }

    },
    components: {
        EditableText
    }
};
</script>

<style>
.box {
    border: 1px solid black;
}
</style>
