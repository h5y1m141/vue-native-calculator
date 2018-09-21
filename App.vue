<template>
  <view class="container">
    <view class="main">
      <button-one :on-add='_onPress' buttonlabel="1" />
      <button-one :on-add='_onPress' buttonlabel="2" />
      <button-one :on-add='_onPress' buttonlabel="3" />
      <button-one :on-add='_onPress' buttonlabel="4" />
      <button-one :on-add='_onPress' buttonlabel="5" />
      <button-one :on-add='_onPress' buttonlabel="6" />
      <button-one :on-add='_onPress' buttonlabel="7" />
      <button-one :on-add='_onPress' buttonlabel="8" />
      <button-one :on-add='_onPress' buttonlabel="9" />
      <view class="calc-container">
        <touchable-opacity :on-press="check" class="calc-button">
          <text class="calc-button-text">+</text>
        </touchable-opacity>
      </view>
      <view class="calc-container">  
        <touchable-opacity :on-press="sum" class="calc-button">
          <text class="calc-button-text">=</text>
        </touchable-opacity>
      </view>
      <view class="calc-container">  
        <touchable-opacity :on-press="clear" class="calc-button">
          <text class="calc-button-text">C</text>
        </touchable-opacity>
      </view>
    </view>
    <view class="sub">
      <text class="button-text">currentLabel: {{ currentLabel }}</text>
      <text class="button-text">firstSelect: {{ selectFirstValue }}</text>
      <text class="button-text">total: {{ total }}</text>
    </view>
  </view>
</template>

<script>
import ButtonOne from './src/buttonOne';
export default {
  components: {
    ButtonOne
  },
  methods: {
    _onPress: function (buttonlabel) {
      this.currentLabel += buttonlabel
    },
    check: function () {
      this.selectFirstValue = this.currentLabel
      this.currentLabel = ''
    },
    sum: function () {
      if (this.currentLabel !=='') {
        this.total = parseInt(this.currentLabel) + parseInt(this.selectFirstValue)
      }
    },
    clear: function () {
      this.currentLabel = ''
      this.selectFirstValue = ''
      this.total = 0
    }
  },
  data: {
    currentLabel: '',
    selectFirstValue: '',
    total: 0
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
.calc-container {
  flex-direction: row;
  padding: 2px;  
}
.calc-button {
  flex: 1;
  background-color: #99ddcc;
  align-items: center;
  justify-content: center;
  max-width: 120px;  
}
.calc-button-text {
  color: white;
  font-weight: bold;
}
</style>
