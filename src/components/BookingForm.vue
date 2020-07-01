<template>
<div class="booking-box">
  <form id="new-booking" v-on:submit="addBooking">
    <h2>New Booking</h2>
    <div>
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name" />
    </div>

    <div>
      <label for="email">Email:</label>
      <input type="text" id="email" v-model="email" />
    </div>

    <div class="cell">
        <div>
            <label for="check">Checked In:</label>
            <input type="checkbox" id="check" v-model="checkedIn" />
        </div>
      <input id="button" type="submit" />
    </div>
  </form>
  </div>
</template>

<script>
import { eventBus } from "../main.js";
import BookingsService from "../services/BookingsService.js";

export default {
  name: "booking-form",
  data() {
    return {
      name: "",
      email: "",
      checkedIn: false
    };
  },
  methods: {
    addBooking(e) {
      e.preventDefault();
      const booking = {
        name: this.name,
        email: this.email,
        checkedIn: this.checkedIn
      };
      BookingsService.postBooking(booking).then(res =>
        eventBus.$emit("booking-added", res)
      );
      e.target.reset();
    }
  }
};
</script>

<style>
#new-booking {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 12px;
  align-items: center;
  justify-items: center;
}

.booking-box {
    border: 1px solid white;
    margin: 1em;
}

.cell {
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-bottom: 1em;
}
.cell input[type="text"] {
  flex: 1;
}

#button {
    margin: 0 auto;
    width: 80%;
}

</style>
