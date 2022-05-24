<template>
<div >

        <h4 class="parameter mx-0 ps-3">Comparisons</h4>

        <div class="container-fluid h-100 p-0">
            
            <div class="row g-0 p-0  d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 " >Columns</p>
                    <div class="dropdown ps-3 col-6 " style="transform: translate(-16px,0);">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
    {{columnNumber}}
  </button>
  <ul class="dropdown-menu " aria-labelledby="dropdownMenuButton1">
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===0}" href="#" @click="ListNum(0)"  >None</a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===1}"  href="#"  @click="ListNum(1)" >&nbsp;1 </a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===2}"  href="#" @click="ListNum(2)">&nbsp;2 </a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===3}"  href="#" @click="ListNum(3)">&nbsp;3 </a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===4}"  href="#" @click="ListNum(4)">&nbsp;4 </a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===5}"  href="#" @click="ListNum(5)">&nbsp;5 </a></li>
            <li><a class="dropdown-item" :class="{bgdark:columnNumber===6}"  href="#" @click="ListNum(6)">&nbsp;6 </a></li>
  </ul>
</div>

            </div>

            <div class="row g-0 p-0 d-flex align-items-baseline " >
                <p class="parameter-label col-6 ps-3">Background</p>
                <div class="d-flex  justify-content-between col-6 align-items-center" >
                    <div class="image-upload">
                        <label for="BackGroundFile">

<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="white" class="bi bi-camera" viewBox="0 0 16 16">
  <path d="M15 12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V6a1 1 0 0 1 1-1h1.172a3 3 0 0 0 2.12-.879l.83-.828A1 1 0 0 1 6.827 3h2.344a1 1 0 0 1 .707.293l.828.828A3 3 0 0 0 12.828 5H14a1 1 0 0 1 1 1v6zM2 4a2 2 0 0 0-2 2v6a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2h-1.172a2 2 0 0 1-1.414-.586l-.828-.828A2 2 0 0 0 9.172 2H6.828a2 2 0 0 0-1.414.586l-.828.828A2 2 0 0 1 3.172 4H2z"/>
  <path d="M8 11a2.5 2.5 0 1 1 0-5 2.5 2.5 0 0 1 0 5zm0 1a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7zM3 6.5a.5.5 0 1 1-1 0 .5.5 0 0 1 1 0z"/>
</svg>
                        </label>
                        <input class="form-control" type="file" accept="image/*" id="BackGroundFile" @change="uploadImg">
                    </div>
                    <input type="color" class="form-control form-control-color border-0" id="exampleColorInput" value="#FFFFFF" @change="changeBackground" style="background: #3e3e46" title="Choose your color">
                    <div></div>
                </div>
            </div>
            
            <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3" >Content Width</p>
                <div class="btns d-flex col-6">
                    <button class="btn  " :class="{bgdark:contentWidth==='small'}"  @click="changeCardWidth('small',$event)" @mouseenter="changeCardWidth('small',$event)" @mouseleave="handleMouseLeave">small</button>
                    <button class="btn " :class="{bgdark:contentWidth==='medium'}" @click="changeCardWidth('medium',$event)"  @mouseenter="changeCardWidth('medium',$event)" @mouseleave="handleMouseLeave">medium</button>
                    <button class="btn " :class="{bgdark:contentWidth==='big'}"  @click="changeCardWidth('big',$event)"  @mouseenter="changeCardWidth('big',$event)" @mouseleave="handleMouseLeave">big</button>
                </div>
            </div>

                        <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3" >Height</p>
                <div class="btns d-flex col-6">
                    <button class="btn  " :class="{bgdark:height==='h-auto'}"  @click="changeCardHeight('h-auto')" >auto</button>
                    <button class="btn " :class="{bgdark:height==='min-vh-75'}" @click="changeCardHeight('min-vh-75')" >50%</button>
                    <button class="btn " :class="{bgdark:height==='min-vh-100'}"  @click="changeCardHeight('min-vh-100')">100%</button>
                </div>
            </div>


</div>
</div>
  
</template>

<script>
export default {
    props : ['length'],

    data(){
        return{
            columnNumber : 3,
            contentWidth : 'big',
            height : 'h-auto'
        }
    },
    methods: {
        addCard () {
            this.$emit('addCard') ;
        },
        changeBackground(e){
            console.log(e.target.value);
            this.$emit('changeBackground',e.target.value)
        },
        changeCardWidth (width,e){
            if(e.type==='click')   this.contentWidth = width
            this.$emit('changeCardWidth',width,e)
        },
        changeCardHeight(height){
            this.height = height
            this.$emit('changeCardHeight',height)
        },
        handleMouseLeave(e){
            this.$emit('handleMouseLeave',e)
        },
        uploadImg(e){
             this.$emit('uploadImgBackground',e)
        },
        ListNum(num){
            this.columnNumber = num
            this.$emit('ListNum',num)

        }
    },
    watch : {
        length : function(){
            this.columnNumber = this.length
        }
    }
}
</script>

<style scoped>
.parameters{
    display: flex;
    align-items: baseline;
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