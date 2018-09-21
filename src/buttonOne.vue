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
    flex-direction: row;
    padding: 2px;  
}
.button {
    flex: 1;
    background-color: #ff3311;
    margin-left: 5px;
    align-items: center;
    justify-content: center;
    padding-top: 5px;
    padding-bottom: 5px;
    max-width: 120px;
}
.button-text {
    color: white;
    font-weight: normal;
}
</style>
