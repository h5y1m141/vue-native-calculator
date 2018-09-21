<template>
  <view class="container">
    <view class="main">
      <view class="button-container">
        <text class="button-text">{{ currentLabel }}</text>
      </view>
    </view>
    <view class="main">
      <button-one :on-add='_onPress' buttonlabel="7" />
      <button-one :on-add='_onPress' buttonlabel="8" />
      <button-one :on-add='_onPress' buttonlabel="9" />
      <view class="calc-container">
        <touchable-opacity :on-press="plus" class="calc-button">
          <text class="calc-button-text">+</text>
        </touchable-opacity>
      </view>
    </view>
    <view class="main">  
      <button-one :on-add='_onPress' buttonlabel="4" />
      <button-one :on-add='_onPress' buttonlabel="5" />
      <button-one :on-add='_onPress' buttonlabel="6" />
      <view class="calc-container">  
        <touchable-opacity :on-press="multiplied" class="calc-button">
          <text class="calc-button-text">x</text>
        </touchable-opacity>
      </view>
    </view>
    <view class="main">  
      <button-one :on-add='_onPress' buttonlabel="1" />
      <button-one :on-add='_onPress' buttonlabel="2" />
      <button-one :on-add='_onPress' buttonlabel="3" />
      <view class="calc-container">  
        <touchable-opacity :on-press="sum" class="calc-button">
          <text class="calc-button-text">=</text>
        </touchable-opacity>
      </view>

    </view>
    <view class="main">
      <button-one :on-add='_onPress' buttonlabel="0" />
      <view class="calc-container"></view>
      <view class="calc-container"></view>
      <view class="calc-container">  
        <touchable-opacity :on-press="clear" class="calc-button">
          <text class="calc-button-text">Clear</text>
        </touchable-opacity>
      </view>
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
      if(this.currentLabel === '0' || this.selectFirstValue) {
        this.currentLabel = buttonlabel
      } else {
        this.currentLabel += buttonlabel
      }
    },
    plus: function () {
      this.symbolsOfOperation = 'plus'
      this.selectFirstValue = this.currentLabel
    },
    multiplied: function () {
      this.symbolsOfOperation = 'multiplied'
      this.selectFirstValue = this.currentLabel
    },
    sum: function () {
      if (this.currentLabel !=='' && this.symbolsOfOperation === 'plus') {
        this.currentLabel = parseInt(this.currentLabel) + parseInt(this.selectFirstValue)
      } else if (this.currentLabel !=='' && this.symbolsOfOperation === 'multiplied') {
        this.currentLabel = parseInt(this.currentLabel) * parseInt(this.selectFirstValue)
      } else {
        this.clear()
      }
    },
    clear: function () {
      this.currentLabel = '0'
      this.selectFirstValue = ''
      this.total = 0
    }
  },
  data: {
    currentLabel: '0',
    selectFirstValue: '',
    symbolsOfOperation: '',
    total: 0
  }
}
</script> 
<style>
.container {
  background-color: #ffffffe1;
  flex: 1;
  padding-top: 50px;
  align-items: center;
}
.button-container {
  flex: 1;
  padding: 2px;
}
.main {
  flex: 1;
  flex-direction: row;
  max-width: 400px;
  align-items: center;
}
.calc-container {
  flex: 1;
  padding: 2px;  
}
.calc-button {
  flex: 1;
  background-color: #99ddcc;
  align-items: center;
  justify-content: center;
  max-width: 80px;
  border-radius: 10px;
}
.calc-button-text {
  color: white;
  font-weight: bold;
  font-size: 24px;
}
.button-text {
  color: #414040;
  font-weight: bold;
  font-size: 32px;
  text-align: right;
  padding: 5px;
}
</style>
