<template>
  <view class="container">
    <touchable-opacity class="button">
      <text class="button-text">{{ buttonlabel }}</text>
    </touchable-opacity>
  </view>
</template>

<script>
export default {
  props: {
    buttonlabel: String
  }
}
</script>

<style>
.container {
  flex: 1;
  padding: 2px;  
}
.button {
  flex: 1;
  margin-left: 5px;
  align-items: center;
  justify-content: center;
  max-width: 80px;
  border-radius: 10px;
}
.button-text {
  color: white;
  font-weight: bold;

}
</style>