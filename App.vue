<template>
  <view class="container">
    <view class="main">
      <button-one buttonlabel="1" />
      <button-one buttonlabel="2" />
      <button-one buttonlabel="3" />
      <button-one buttonlabel="4" />
      <button-one buttonlabel="5" />
      <button-one buttonlabel="6" />
      <button-one buttonlabel="7" />
      <button-one buttonlabel="8" />
      <button-one buttonlabel="9" />
    </view>
  </view>
</template>

<script>
import ButtonOne from './src/buttonOne';
export default {
  components: {
    ButtonOne
  }
}
</script> 
<style>
.container {
  background-color: #ddd;
  flex: 1;
  padding-top: 50px;
  align-items: center;
}
.main {
  flex: 1;
  max-width: 400px;
  align-items: center;
}
</style>
