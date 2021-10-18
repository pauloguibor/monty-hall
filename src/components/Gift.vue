<template>
  <div class="gift">
      <div class="gift-tie1"></div>
      <div class="gift-tie2"></div>
      <div class="gift-top"></div>
      <div class="gift-body"></div>
  </div>
</template>

<script>
export default {
    name: 'Gift'
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
    .gift-top{
        width: 100px;
        height: 25px;
        background-color: #5c7e;
    }
    .gift-body{
        width: 90px;
        height: 60px;
        background-color: #5c7e32;
    }
    .gift-tie1{
        position: absolute;
        width: 15px;
        height: 85px;
        background-color: red;
    }
    .gift-tie2{
        position: absolute;
        top: 40px;
        width: 90px;
        height: 15px;
        background-color: red;
    }
</style>