<template>
  <div id="window">
    <TitleBar :settings="titlebar"></TitleBar>
    <div class="window-body">
      <div class="main">
        <div class="tool-bar"></div>
      </div>
      <div class="bottom-bar">
        <ColorPicker :colors="colors" :colorMain="colorMain" :colorSecond="colorSecond" @switchColors="switchColors()" @mainColorChange="setMainColor" @secondColorChange="setSecondColor" @changeColor="setColor"></ColorPicker>
      </div>
    </div>
  </div>
</template>

<script>
import TitleBar from './components/TitleBar.vue'
import ColorPicker from './components/ColorPicker.vue'
import iconImage from "@/assets/paint.png";
export default {
  name: 'App',
  components: {
    TitleBar,
    ColorPicker,
  },
  data: function () {
    return {
      titlebar: {
        title:"OnlinePaint",
        icon:iconImage,
        controls: {
          close:true,
          minimize:true,
          maximize:true,
        }
      },
      colors:["#020000","#817E7D","#7B000C","#7C800F","#018305","#017D81","#020084","#770381","#7E804B","#043F32","#077DFF","#014282","#8306EF","#7E4202",
              "#FCFAF6","#C2C0BA","#EF0A03","#FEFF09","#06F805","#00FFF9","#0802F3","#F20BF1","#F8FF89","#0CF989","#92F8F8","#897EF8","#EC0B77","#F78541"],
      colorMain:"#020000",
      colorSecond:"#FCFAF6",
    }
  },
  methods: {
    switchColors(){
      var temp = this.colorMain;
      this.colorMain = this.colorSecond;
      this.colorSecond = temp;
    },
    setMainColor(color){
      this.colorMain = color;
    },
    setSecondColor(color){
      this.colorSecond = color;
    },
    setColor(i, e){
      this.colors[i] = e.target.value;
      this.colorMain = e.target.value;
    }
  }
}

</script>


<style>
#window {
  box-shadow: inset -1px -1px #00138c, inset 1px 1px #0831d9, inset -2px -2px #001ea0, inset 2px 2px #166aee, inset -3px -3px #003bda, inset 3px 3px #0855dd;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
  padding: 0 0 3px;
  -webkit-font-smoothing: antialiased;
  background: #ece9d8;
}

.window-body {
  margin: 8px;
}

</style>
