<template>

<div>
    <h4 class="parameter mx-0 ps-3">Inline Text</h4>

      <div class="inline-text ps-3">
        <div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
    Dropdown button
  </button>
  <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" href="#">normal</a></li>
        <li><a class="dropdown-item" href="#">header 1 </a></li>
        <li><a class="dropdown-item" href="#">header 2</a></li>
        <li><a class="dropdown-item" href="#">header 4</a></li>
        <li><a class="dropdown-item" href="#">header 6</a></li>
  </ul>
</div>

<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-type-bold icon m-2" viewBox="0 0 16 16">
  <path d="M8.21 13c2.106 0 3.412-1.087 3.412-2.823 0-1.306-.984-2.283-2.324-2.386v-.055a2.176 2.176 0 0 0 1.852-2.14c0-1.51-1.162-2.46-3.014-2.46H3.843V13H8.21zM5.908 4.674h1.696c.963 0 1.517.451 1.517 1.244 0 .834-.629 1.32-1.73 1.32H5.908V4.673zm0 6.788V8.598h1.73c1.217 0 1.88.492 1.88 1.415 0 .943-.643 1.449-1.832 1.449H5.907z"/>
</svg>
<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-type-italic icon m-2" viewBox="0 0 16 16">
  <path d="M7.991 11.674 9.53 4.455c.123-.595.246-.71 1.347-.807l.11-.52H7.211l-.11.52c1.06.096 1.128.212 1.005.807L6.57 11.674c-.123.595-.246.71-1.346.806l-.11.52h3.774l.11-.52c-1.06-.095-1.129-.211-1.006-.806z"/>
</svg>
<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-type-underline icon m-2" viewBox="0 0 16 16">
  <path d="M5.313 3.136h-1.23V9.54c0 2.105 1.47 3.623 3.917 3.623s3.917-1.518 3.917-3.623V3.136h-1.23v6.323c0 1.49-.978 2.57-2.687 2.57-1.709 0-2.687-1.08-2.687-2.57V3.136zM12.5 15h-9v-1h9v1z"/>
</svg>
<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-type-strikethrough icon m-2" viewBox="0 0 16 16">
  <path d="M6.333 5.686c0 .31.083.581.27.814H5.166a2.776 2.776 0 0 1-.099-.76c0-1.627 1.436-2.768 3.48-2.768 1.969 0 3.39 1.175 3.445 2.85h-1.23c-.11-1.08-.964-1.743-2.25-1.743-1.23 0-2.18.602-2.18 1.607zm2.194 7.478c-2.153 0-3.589-1.107-3.705-2.81h1.23c.144 1.06 1.129 1.703 2.544 1.703 1.34 0 2.31-.705 2.31-1.675 0-.827-.547-1.374-1.914-1.675L8.046 8.5H1v-1h14v1h-3.504c.468.437.675.994.675 1.697 0 1.826-1.436 2.967-3.644 2.967z"/>
</svg>
   

  <input type="color" class="form-control form-control-color border-0 " id="exampleColorInput" value="#2b2b33" @change="changetextColor" style="background: #3e3e46" title="Choose your color">
 
      </div>

        <div class="dropdown ps-3">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
    Dropdown button
  </button>
  <ul class="dropdown-menu " aria-labelledby="dropdownMenuButton1">
        <li><a class="dropdown-item" href="#">default</a></li>
        <li><a class="dropdown-item" href="#">&nbsp;8 </a></li>
        <li><a class="dropdown-item" href="#">10</a></li>
        <li><a class="dropdown-item" href="#">14</a></li>
        <li><a class="dropdown-item" href="#">16</a></li>
  </ul>
</div>


</div>
</template>

<script>
export default {
    methods: {
        changeText(a) {
            this.$emit('changeText',a) ;
        },
        changeWeight(a){
          this.$emit('changeWeight',a)
        },
        changetextColor(a){
          this.$emit('changetextColor',a.target.value);
        },
        changeFontSize(a){
          this.$emit('changeFontSize',a);
        }
    }
}
</script>

<style scoped >
.icon{
  cursor:pointer;
  background: #595964;
  transform: scale(1.4);
  border : 1px solid black;
  margin-left : 3px;
}
.inline-text{
  display: flex;
  align-items: center;
}
.parameters{
    display: flex;
    align-items: baseline;
}

button:not(:disabled), [type=button]:not(:disabled), [type=reset]:not(:disabled), [type=submit]:not(:disabled){
    font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
    padding : .3em 1.2em;
    margin : .3em 0;

}
#dropdown-1, #dropdown-2 {
    font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
    padding : 0;
    margin : 0 0;
        background: #3b3b43 !important;
    border : 1px solid black !important;
    box-shadow: none !important;

}
.btn-check:focus + .btn-secondary, .btn-secondary:focus{
    background: #3b3b43 !important;
    border : 1px solid black !important;
    box-shadow: none !important;
}
.parameter {
    font-size: 1em;
    background: #2b2b33;
    padding: .3em;
    color : white;
    margin : 1em 0;
}
.parameter-label {
    color : rgba(255, 255, 255, 0.897);
    font-size: 12px;
}


.btn-group > .btn, .btn-group-vertical > .btn{
    font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
}
.dropdown-item {
  font-size : 8px;
    border : none;
    outline : none;

}
input[type=color].form-control {
    padding : 6px !important;
}
.form-control-color:not(:disabled):not([readonly]){
    box-shadow : none;
}
.btns{
        justify-content : space-between;

}
.image-upload>input {
  display: none;
}
</style>
