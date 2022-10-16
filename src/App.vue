<template>
  <div id="window">
    <TitleBar :settings="titlebar"></TitleBar>
    <div class="window-body">
      <p>There's so much room for activities!</p>
    </div>
  </div>
</template>

<script>
import TitleBar from './components/TitleBar.vue'
import iconImage from "@/assets/paint.png";
export default {
  name: 'App',
  components: {
    TitleBar,
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
      }
    }
  }  
};
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
