<template>
  <div class="box">
    <div id="name">
        <label>Name: </label>
        <EditableText :value="booking.name" v-on:edited="editedName"/>
    </div>
    <div id="checked-in">
        <label for="checkbox">Checked In:</label>
        <input type="checkbox" v-model="booking.checkedIn" v-on:change="updateBooking" id="checkbox">
    </div>
    <div id="email">
        <label>Email: </label>
        <EditableText :value="booking.email" v-on:edited="editedEmail"/>
    </div>
    <button id="delete-button" name="delete" v-on:click="deleteBooking">Delete</button>
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
    border: 1px solid white;
    margin: 1em;
    display: grid;
    grid-template-columns: 5fr 1fr;
    padding: 5px;
}

#checked-in {
    justify-self: right;
}

#delete-button {
    width: fit-content;
    justify-self: right;
    background: rgba(220, 20, 60, 0.603);
    color: white;
}

label {
    display: inline-block;
    font-weight: bold;
    margin: 0px 5px 0px 0px;
}

</style>
