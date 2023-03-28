<template>
  <div class="main">
    <div class="palka"></div>
    <div class="palka" style="transform: rotate(-90deg);"></div>
  </div>
</template>

<script>export default {
  name: 'NewTimer',
  props: {},

}</script>

<style scoped>
.main {
  width: 225px;
  height: 120px;
  line-height: 120px;
  text-align: center;
  vertical-align: center;
  background: rgba(105, 105, 105, 1);
  color: rgba(158, 158, 158, 1);
  font-size: large;
  position: relative;
  margin-left: 50px;
  margin-bottom: 45px;
}

.palka{
  position: absolute;
  top: 50px;
  left: 103px;
  width: 3px;
  height: 20px;
  background: #9E9E9E;
}

</style>
