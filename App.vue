<template>
  <view class="container">
    <view class="main">
      <view class="button-container">
        <text class="button-text">{{ currentLabel }}</text>
      </view>
    </view>
    <view class="main">
      <button-number :on-add='_onPress' buttonlabel="7" />
      <button-number :on-add='_onPress' buttonlabel="8" />
      <button-number :on-add='_onPress' buttonlabel="9" />
      <button-symbols-of-operation :detect-button='plus' buttonlabel="+" />
    </view>
    <view class="main">  
      <button-number :on-add='_onPress' buttonlabel="4" />
      <button-number :on-add='_onPress' buttonlabel="5" />
      <button-number :on-add='_onPress' buttonlabel="6" />
      <button-symbols-of-operation :detect-button='multiplied' buttonlabel="x" />
    </view>
    <view class="main">  
      <button-number :on-add='_onPress' buttonlabel="1" />
      <button-number :on-add='_onPress' buttonlabel="2" />
      <button-number :on-add='_onPress' buttonlabel="3" />
      <button-symbols-of-operation :detect-button='sum' buttonlabel="=" />
    </view>
    <view class="main">
      <button-number :on-add='_onPress' buttonlabel="0" />
      <fake-button buttonlabel="1" />
      <fake-button buttonlabel="2" />
      <button-symbols-of-operation :detect-button='clear' buttonlabel="Clear" />
    </view>
  </view>
</template>

<script>
import ButtonNumber from './src/ButtonNumber';
import ButtonSymbolsOfOperation from './src/ButtonSymbolsOfOperation';
import FakeButton from './src/FakeButton';

export default {
  components: {
    ButtonNumber,
    ButtonSymbolsOfOperation,
    FakeButton
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
.button-text {
  color: #414040;
  font-weight: bold;
  font-size: 32px;
  text-align: right;
  padding: 5px;
}
</style>
