<template>
  <view class="container">
    <touchable-opacity :on-press="detectButton" class="button">
      <image class="image-icon" :source="image" />
      <text class="text">{{ buttonlabel }}円</text>
    </touchable-opacity>
  </view>
</template>

<script>
import image2 from './resources/img/2_128x128.png'
import image3 from './resources/img/3_128x128.png'
import image4 from './resources/img/3_128x128.png'
import image5 from './resources/img/5_128x128.png'
import image6 from './resources/img/6_128x128.png'
import image7 from './resources/img/7_128x128.png'
import image8 from './resources/img/8_128x128.png'
import image9 from './resources/img/9_128x128.png'
import image10 from './resources/img/10_128x128.png'
import image11 from './resources/img/11_128x128.png'

export default {
  props: {
    buttonlabel: String,
    icon: String,
    onAdd: Function
  },
  methods: {
    detectButton: function () {
      this.onAdd(this.buttonlabel)
    }
  },
  data: function () {
    let icons = [
      {id: 3, image: image3},
      {id: 4, image: image4},
      {id: 5, image: image5},
      {id: 6, image: image6},
      {id: 7, image: image7},
      {id: 8, image: image8},
      {id: 9, image: image9},
      {id: 10, image: image10},
      {id: 11, image: image11},
    ]
    return {
      image: icons.filter(icon => icon.id === Number(this.icon))[0].image
    }
  }
}
</script>

<style>
.container {
  flex: 1;
  padding: 5px;
  max-height: 100px;
  margin: 1px;
}
.button {
  flex: 1;
  margin-left: 5px;
  align-items: center;
  justify-content: center;
  max-width: 120px;
  max-height: 120px;
  padding: 1px;
}
.image-icon {
  width: 72px;
  height: 72px;
}
.text {
  color: #414040;
  font-weight: bold;
  font-size: 16px;
  text-align: right;
  padding: 5px;
}
</style>
