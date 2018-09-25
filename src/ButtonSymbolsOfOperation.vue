<template>
  <view class="calc-container">
    <touchable-opacity :on-press="select" class="calc-button">
      <text class="calc-button-text">{{ buttonlabel }}</text>
    </touchable-opacity>
  </view>
</template>
<script>
export default {
  props: {
    buttonlabel: String,
    detectButton: Function
  },
  methods: {
    select () {
      this.detectButton(this.buttonlabel)
    }
  }
}
</script>
<style>
.calc-container {
  flex: 1;
  padding: 2px;  
}
.calc-button {
  flex: 1;
  background-color: #99ddcc;
  margin-left: 5px;
  align-items: center;
  justify-content: center;
  max-width: 80px;
  max-height: 80px;
  border-radius: 10px;
}
.calc-button-text {
  color: white;
  font-weight: bold;
  font-size: 24px;
}
</style>
