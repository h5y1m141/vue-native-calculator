<template>
  <view class="container">
    <view class="main">
      <view class="button-container">
        <text class="button-text">{{ currentLabel }}円</text>
      </view>
    </view>
    <view class="main">
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'3000'" :icon="'11'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'600'" :icon="'3'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'400'" :icon="'5'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'500'" :icon="'6'"/>
      </view>
    </view>
    <view class="main">
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'500'" :icon="'7'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'600'" :icon="'4'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'1500'" :icon="'8'"/>
      </view>
      <view>
        <button-sweet :on-add='_onPress' :buttonlabel="'100'" :icon="'10'"/>
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
import ButtonSweet from './src/ButtonSweet'

export default {
  components: {
    ButtonNumber,
    ButtonSymbolsOfOperation,
    FakeButton,
    ButtonSweet
  },
  methods: {
    _onPress(buttonlabel) {
      if (!this.isValueSelected) {
        this.currentLabel = buttonlabel
        this.isValueSelected = true
      } else {
        this.currentLabel += buttonlabel
      }
    },
    plus() {
      this.symbolsOfOperation = 'plus'
      this.selectFirstValue = this.currentLabel
      this.isValueSelected = false
    },
    multiplied() {
      this.symbolsOfOperation = 'multiplied'
      this.selectFirstValue = this.currentLabel
      this.isValueSelected = false
    },
    sum() {
      if (this.currentLabel !=='' && this.symbolsOfOperation === 'plus') {
        this.currentLabel = parseInt(this.currentLabel) + parseInt(this.selectFirstValue)
      } else if (this.currentLabel !=='' && this.symbolsOfOperation === 'multiplied') {
        this.currentLabel = parseInt(this.currentLabel) * parseInt(this.selectFirstValue)
      } else {
        this.clear()
      }
    },
    clear() {
      this.currentLabel = '0'
      this.selectFirstValue = ''
      this.isValueSelected = false
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
  padding-top: 20px;
  align-items: center;
}
.button-container {
  flex: 1;
  padding: 2px;
  max-height: 120px;
}
.main {
  flex: 1;
  flex-direction: row;
  align-items: center;
}
.button-text {
  color: #414040;
  font-weight: bold;
  font-size: 32px;
  text-align: right;
  padding: 5px;
}
.button {
  flex: 1;
  margin-left: 5px;
  align-items: center;
  justify-content: center;
  max-width: 80px;
  max-height: 80px;
  border-radius: 10px;
}
.image-icon {
  width: 72px;
  height: 72px;
}

</style>
