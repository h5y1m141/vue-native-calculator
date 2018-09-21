<template>
  <view class="container">
    <touchable-opacity :on-press="detectButton" class="button">
      <text class="button-text">{{ buttonlabel }}</text>
    </touchable-opacity>
  </view>
</template>

<script>
export default {
  props: {
    buttonlabel: String,
    onAdd: Function
  },
  methods: {
    detectButton: function () {
      this.onAdd(this.buttonlabel)
    }
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
  background-color: #f3a8e3f6;
  margin-left: 5px;
  align-items: center;
  justify-content: center;
  padding-top: 5px;
  padding-bottom: 5px;
  max-width: 80px;
  border-radius: 10px;
}
.button-text {
  color: white;
  font-weight: normal;
  font-size: 24px;
}
</style>
