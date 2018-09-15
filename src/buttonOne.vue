<template>
  <view class="container">
    <touchable-opacity :on-press="check" class="button">
      <text class="button-text">{{ buttonlabel }}</text>
    </touchable-opacity>
  </view>
</template>

<script>
export default {
  props: [
    'buttonlabel'
  ],
  methods: {
    check: function () {
      alert("hello"+ this.buttonlabel)
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
    max-width: 80px;
}
.button-text {
    color: white;
    font-weight: normal;
}
</style>
