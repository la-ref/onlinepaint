<template>
  <div class="top-bar">
      <img v-if="settings.icon != null" :src="settings.icon"/>
      <h1 class="title-bar">{{settings.title}}</h1>
      <div class="title-filler"></div>
      <div class="title-bar-controls">
        <button v-if="settings.controls.minimize" class="minimize"></button>
        <button v-if="settings.controls.maximize" class="maximize"></button>
        <button v-if="settings.controls.close" class="close"></button>
      </div>
    </div>
</template>

<script>
export default {
  name: "TitleBar",
  props: ["settings"],
}
</script>

<style>


.top-bar {
  display: flex;
  align-items: center;
  background: linear-gradient(180deg,#0997ff,#0053ee 8%,#0050ee 40%,#06f 88%,#06f 93%,#005bff 95%,#003dd7 96%,#003dd7);
  padding: 3px 5px 3px 3px;
  border-top: 1px solid #0831d9;
  border-left: 1px solid #0831d9;
  border-right: 1px solid #001ea0;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
  font-size: 13px;
  text-shadow: 1px 1px #0f1089;
  height: 21px;
}

.title-filler{
  flex-grow:1;
}

.title-bar {
  font-family: Trebuchet MS;
  font-size: 13px;
  text-shadow: 1px 1px #0f1089;
  color: white;
  margin-right: 24px;
  padding-left: 4px;
  letter-spacing: 0;
  font-weight: 700;
}

img {
  width: 16px;
  height: 16px;
}

.title-bar-controls{
  display: flex;
}

.title-bar-controls button{
  min-width: 21px;
  min-height: 21px;
  margin-left: 2px;
  background-repeat: no-repeat;
  background-position: 50%;
  box-shadow: none;
  background-color: #0050ee;
  transition: background .1s;
  border: none;
}

.close {
  background-image: url("../assets/svg/close.svg");
}
.close:hover {
  background-image: url("../assets/svg/closehover.svg");
}
.close:not(:disabled):active {
  background-image: url("../assets/svg/closeactive.svg");
}

.minimize{
  background-image: url("../assets/svg/minimize.svg");
}
.minimize:hover{
  background-image: url("../assets/svg/minimizehover.svg");
}
.minimize:not(:disabled):active {
  background-image: url("../assets/svg/minimizeactive.svg");
}

.maximize{
  background-image: url("../assets/svg/maximize.svg");
}
.maximize:hover{
  background-image: url("../assets/svg/maximizehover.svg");
}
.maximize:not(:disabled):active {
  background-image: url("../assets/svg/maximizeactive.svg");
}
</style>