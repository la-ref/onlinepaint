<template>
<div class="bottom-bar">
    <div class="color-bar">
        <div class="mycolors" @mousedown="$emit('switchColors')" >
        <div class="maincolor" :style="{ 'background-color': colorMain }"></div>
        <div class="secondcolor" :style="{ 'background-color': colorSecond }"></div>
        </div>
        <div class="colors">
            <input v-for="(color,k) in colors"  :key="color" type="color" :value="color" v-on:click="onClick($event); $emit('mainColorChange',color)" @contextmenu.prevent="$emit('secondColorChange',color)" @change="$emit('changeColor',k,$event)">
        </div>
    </div>
</div>
</template>

<script>
export default {
  name: "ColorPicker",
  props: ["colors","colorMain","colorSecond"],
  data: function(){
    return {
        clicks: 0,
        timer: null,
    }
  },
  methods: {
    onClick(e) {
        this.clicks++;
        if (this.clicks === 1) {
            this.timer = setTimeout( () => {
            this.clicks = 0
            }, 200);
            e.preventDefault();
        } else {
            clearTimeout(this.timer);  
            this.clicks = 0;
        }         
        },
    }
}
</script>

<style>

.colors {
  display: flex;
  flex-wrap: wrap;
  width: 238px;
}

input[type="color"] {
  -webkit-appearance: none;
  border: none;
  width: 16px;
  height: 16px;
  padding: 0;
  border: 1px solid rgba(149, 149, 149, 0.5);
  outline: 0.8px solid #ece9d8;;
  margin-bottom: 1px;
  margin-right: 1px;
}

input[type="color"]::-webkit-color-swatch-wrapper {
	padding: 0;
}
input[type="color"]::-webkit-color-swatch {
	border: none;
  padding: 0;
  border-top: 1px solid black;
  border-left: 1px solid black;
}

.mycolors{
  width: 30px;
  height: auto;
  background-color: #F5F4EB;
  border-top: 1px solid black;
  border-left: 1px solid black;
  margin-right: 2px;
  outline: 1px solid rgba(149, 149, 149, 0.5);
  margin-bottom: 2px;
  margin-top: 1px;
}

.color-bar {
  display: flex;
}

.mycolors div {
  position: relative;
  width: 13px;
	height: 13px;
  border-top: 1px solid #ffffff;
  border-left: 1px solid #ffffff;
  border-right: 1px solid#565656;
  border-bottom: 1px solid#565656;
}

.mycolors div:before {
  content: "";
  display: block;
  padding: 5.5px 0;
  border: 1px solid #ece9d8; 

}
.maincolor {
  left: 10%;
  top:4px;
  z-index: 5;
}

.secondcolor {
  left: 38%;
  top:-4px;
}

</style>