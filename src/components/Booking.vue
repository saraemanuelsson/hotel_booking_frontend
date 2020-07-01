<template>
  <div class="box">
    <div>
        <label>Name:</label>
        <p>{{ booking.name }}</p>
    </div>
    <div>
        <label>Email:</label>
        <p>{{ booking.email }}</p>
    </div>
    <div>
        <label>Checked in:</label>
        <p>{{ booking.checkedIn }}</p>
    </div>
  </div>
</template>

<script>
export default {

    props: ["booking"]
};
</script>

<style>
.box {
    border: 1px solid black;
}
</style>
