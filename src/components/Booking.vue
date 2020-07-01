<template>
  <div class="box">
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
