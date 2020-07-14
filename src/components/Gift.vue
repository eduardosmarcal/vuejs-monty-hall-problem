<template>
  <div class="gift">
    <div class="gift-tie-1"></div>
    <div class="gift-tie-2"></div>
    <div class="gift-top"></div>
    <div class="gift-body"></div>
  </div>
</template>

<script>
export default {
  name: 'Gift',
}
</script>

<style>
.gift {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 10;
}

.gift-top {
  background-color: #7aa944;
  height: 25px;
  width: 100px;
}

.gift-body {
  background-color: #5c7e32;
  height: 60px;
  width: 90px;
}

.gift-tie-1 {
  background-color: red;
  height: 85px;
  width: 15px;
  position: absolute;
}

.gift-tie-2 {
  background-color: red;
  position: absolute;
  top: 40px;
  width: 90px;
  height: 15px;
}
</style>