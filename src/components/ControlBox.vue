<template>
<div>
  <h4 class="parameter mx-0 ps-3">Media</h4>
    <div class="container h-100 p-0">


        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Colors</p>
    <input type="color" class="form-control form-control-color border-0 ms-4" id="exampleColorInput"  v-model="bgColor" @change="changeBoxBackground" style="background: #3e3e46;transform: translate(-33px, 6px);" title="Choose your color">
        </div>
        <div class="row g-0 p-0 d-flex align-items-baseline ">
            
            <p class="parameter-label col-6 ps-3 ">Button</p>
            <div class="icns col-6">
<svg xmlns="http://www.w3.org/2000/svg" @click="handleCardButton('add')" style="cursor : pointer"  width="20" height="20" fill="black" class="bi bi-plus" viewBox="0 0 16 16">
  <path d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z"/>
</svg>
<svg xmlns="http://www.w3.org/2000/svg"  @click="handleCardButton('del')" style="cursor : pointer"  width="20" height="20" fill="black" class="bi bi-trash-fill" viewBox="0 0 16 16">
  <path d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1H2.5zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5zM8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5zm3 .5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 1 0z"/>
</svg>


<div></div>
            </div>
        </div>

        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Border</p>
            <div class="d-flex col-6 justify-content-between">
                <div class="borderControl mx-0">
                    <input type="number"  min="0" max="100" v-model="width"  @change="handleBorder($event,'width')"/>
                    <span>px</span>
                </div>
                <input type="color" class="form-control form-control-color border-0 m-0" id="exampleColorInput" v-model="color" @change="handleBorder($event,'color')" style="background: #3e3e46" title="Choose your color">
                <div>
                     <div class="dropdown ps-3 col-6 " >
                    <button class="btn btn-secondary dropdown-toggle w-100 mt-1" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                        </button>
                    <ul class="dropdown-menu col-6" aria-labelledby="buttonSize">
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('solid')">solid</a></li>
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('dotted')">dotted</a></li>
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('dashed')">dashed</a></li>
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('groove')">groove</a></li>
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('ridge')">ridge</a></li>
                        <li><a class="dropdown-item" href="#" @click="handleBorderStyle('inset')">inset</a></li>
                    </ul>
                </div>
                </div>
            </div>
        </div>

        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Round Corners</p>
                <div class="borderControl col-6">
                    <input type="number"  min="0" max="100" v-model="radius" @change="handleBorder($event,'radius')"/>
                    <span>px</span>
                </div>
        </div>

                    <div class="row g-0 p-0 align-items-baseline shadow-div">
                <p class="parameter-label col-6 ps-3" >Shadow</p>
                <div class="d-flex col-6">
                    <button class="btn" :class="{focused:!active,bgdark:!active}" @click="handleShadowBtn">None</button>
                     <button class="btn" :class="{focused:active,bgdark:active}"  @click="handleShadowBtn"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Capa_1" x="0px" y="0px" width="55.832px" height="55.832px" viewBox="0 0 55.832 55.832" style="enable-background:new 0 0 55.832 55.832;" xml:space="preserve"><g><g><g><path d="M9.166,41.832H6.669C2.991,41.832,0,38.84,0,35.163V11.835c0-3.678,2.992-6.669,6.669-6.669h34.328     c3.678,0,6.669,2.992,6.669,6.669v3.164c0,0.552-0.448,1-1,1H14.835c-2.575,0-4.669,2.095-4.669,4.669v20.164     C10.166,41.385,9.718,41.832,9.166,41.832z M6.669,7.166C4.094,7.166,2,9.261,2,11.835v23.328c0,2.575,2.095,4.669,4.669,4.669     h1.497V20.669c0-3.678,2.992-6.669,6.669-6.669h30.831v-2.164c0-2.575-2.096-4.669-4.669-4.669H6.669V7.166z"></path><path d="M49.163,50.666H14.835c-3.678,0-6.669-2.992-6.669-6.669V20.669c0-3.678,2.992-6.669,6.669-6.669h34.328     c3.678,0,6.669,2.992,6.669,6.669v23.328C55.832,47.674,52.84,50.666,49.163,50.666z M14.835,15.999     c-2.575,0-4.669,2.095-4.669,4.669v23.328c0,2.575,2.095,4.669,4.669,4.669h34.328c2.575,0,4.669-2.095,4.669-4.669V20.669     c0-2.575-2.096-4.669-4.669-4.669L14.835,15.999L14.835,15.999z"/></g></g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g></svg></button>
               </div>       
                </div>

                <div class="shadow-options" v-if="active">

                             <div class="row g-0 p-0 d-flex ">
                                    <p class="parameter-label col-6 ps-3 " style="transform: translate(0, 10px);">&nbsp;&nbsp;⌙ Color</p>
            <input @change="handleShadow($event,'color')" type="color" class="form-control form-control-color border-0 m-0" v-model="shadowColor" style="background: #3e3e46" title="Choose your color">
                                </div>

                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Offset (X, Y)</p>
                                        <div class="borderControl col-6 me-1">
                                            <input type="number" v-model="offsetX" min="0" max="100" @change="handleShadow($event,'x')"/>
                                            <span>px</span>
                                        </div> 
                                        <div class="borderControl col-6">
                                            <input type="number" v-model="offsetY" min="0" max="100" @change="handleShadow($event,'y')"/>
                                            <span>px</span>
                                        </div>
                                </div>
                                
                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Blur</p>
                                        <div class="borderControl col-6">
                                            <input type="number"  v-model="blur" min="0" max="100" @change="handleShadow($event,'blur')"/>
                                            <span>px</span>
                                        </div>
                                </div>
                            
                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Spread</p>
                                        <div class="borderControl col-6">
                                            <input type="number" v-model="spread"  min="0" max="100" @change="handleShadow($event,'spread')"/>
                                            <span>px</span>
                                        </div>
                                </div>
                        </div>
               </div>
           
               
           </div>



</template>

<script>
export default {
    props : ['boxes','focusOn'],
    data(){
        return{
            width : 0,
            bgColor : "#000000",
            radius : 0,
            color : "#000000",
            active : false,
            spread : 0,
            blur : 0,
            offsetX : 0,
            offsetY : 0,
            shadowColor : "#000000"
        }
    },
    methods:{
        changeBoxBackground(e){
            this.$emit('changeBoxBackground',e.target.value)
        },
        handleCardButton(action){
            this.$emit('handleCardButton',action)
        },
        uploadImg(e){
             this.$emit('uploadImg',e)
        },
        handleBorder(e,type){
            this.$emit('handleBorder',e.target.value,type)
        },
        handleBorderStyle(style){
             this.$emit('handleBorderStyle',style)
        },
        handleShadowBtn(e){
            if(e.target.textContent == 'None'){
            this.active = false
            this.spread = this.blur = this.offsetX = this.offsetY = 0
            this.shadowColor = "#000000"
            this.$emit('handleShadowBtn',false)

            }
            else{
                   this.active = true
                   this.$emit('handleShadowBtn',true)

            }
        },
        handleShadow(e,option){
                this.$emit('handleShadow',e.target.value,option)
        }
    },
    watch : {
        focusOn : function()
        {
            console.log(this.focusOn)
                 this.boxes.map(card =>{
                 if(card.id === this.focusOn){
                this.bgColor = card.bgColor
                this.active = card.shadow.active
                this.spread = card.shadow.spread
                this.blur = card.shadow.blur

                this.shadowColor = card.shadow.color
                this.offsetX = card.shadow.offset.x
                this.offsetY = card.shadow.offset.y

                this.width = card.border.width
                this.radius = card.border.radius
                this.color = card.border.color
                return
                }})
                
        }
    }

}
</script>

<style scoped>
.bgdark{
    background: #2b2b33 !important;
    color : white !important;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
svg{
    cursor : pointer;
}
.icns{
    display: flex;
    justify-content: space-between;
}
input[type="number"]{
    box-sizing: content-box;
    padding: 2px;
    border: none;
    outline : none;
    overflow: hidden;
    border-radius: 0;
    background-color: transparent;
    -moz-appearance: textfield;
    color : white;

}
.borderControl{
    margin-top : 7px;
    border: 1px solid #000000;
    border-radius: 2px;
    background-color: #2b2b33;
    max-width: 40px;
    height : 25px;
    display : flex;
    align-items: center;
    font-size: 12px;
}

span{
    margin-right: 2px;
    color: #60606b;
}
.shadow-div svg{
    fill:white;
    width : 20px;
    height : 20px;
}
.focused{
    background : #3e3e46;
}
.bgdark{
    background: #2b2b33 !important;
    color : white !important;
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
  font-size : 10px;
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