<template>

<div>
    <h4 class="parameter mx-0 ps-3">Inline Text</h4>

      <div class="inline-text ps-3">
        <b-dropdown id="dropdown-1" size="sm" text="Choose size" class="me-2">
    <b-dropdown-item @click="changeText('n')">normal</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-1')" >header 1 </b-dropdown-item>
    <b-dropdown-item @click="changeText('display-2')">header 2</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-4')">header 4</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-6')">header 6 </b-dropdown-item>
      </b-dropdown>

      <b-icon ref="icon" class="icon me-2" variant="light" icon="type-bold" aria-hidden="true"  @click="changeWeight('fw-bold')" ></b-icon>
  <b-icon ref="icon" class="icon me-2" variant="light" icon="type-italic" aria-hidden="true"  @click="changeWeight('fst-italic')" ></b-icon>
  <b-icon ref="icon" class="icon me-2" variant="light" icon="type-underline" aria-hidden="true" @click="changeWeight('text-decoration-underline')" ></b-icon>
  <b-icon ref="icon" class="icon me-2" variant="light" icon="type-strikethrough" aria-hidden="true" @click="changeWeight('text-decoration-line-through')" ></b-icon>
  <input type="color" class="form-control form-control-color border-0 " id="exampleColorInput" value="#2b2b33" @change="changetextColor" style="background: #3e3e46" title="Choose your color">
 
      </div>

      <b-dropdown id="dropdown-2" size="sm" text="font size" class=" ms-3">
    <b-dropdown-item @click="changeFontSize('inherit')">default</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('8px')">&nbsp;8</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('10px')">10 </b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('12px')">12</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('14px')">14</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('16px')">16 </b-dropdown-item>
      </b-dropdown>
      
    <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
    <li><a class="dropdown-item" href="#">Action</a></li>
    <li><a class="dropdown-item" href="#">Another action</a></li>
    <li><a class="dropdown-item" href="#">Something else here</a></li>
  </ul>
 
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
    color : white;
    background : #595964;
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
