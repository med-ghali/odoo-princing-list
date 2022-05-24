<template>
  <div class="container-fluid  p-0">
            
            <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 ">Button Size</p>
                <div class="dropdown ps-3 col-6 " >
                    <button class="btn btn-secondary dropdown-toggle w-100" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                        {{buttonSize}}</button>
                    <ul class="dropdown-menu col-6" aria-labelledby="buttonSize">
                        <li><a class="dropdown-item" href="#" @click="changeButtonSize('Small')">Small</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonSize('Medium')">Medium</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonSize('Large')">Large</a></li>
                    </ul>
                </div>
            </div>

            <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 ">Button Color</p>                
                <div class="dropdown ps-3 col-6 " >
                    <button class="btn btn-secondary dropdown-toggle w-100" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
                        {{buttonColor}}</button>
                    <ul class="dropdown-menu col-6" aria-labelledby="buttonSize">
                        <li><a class="dropdown-item" href="#"  @click="changeButtonColor('Blue','btn-primary')">Blue</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Red','btn-danger')">Red </a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Green','btn-success')">Green</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Black','btn-dack')">Black</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Light','btn-light')">Light</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Warning','btn-warning')">Warning</a></li>
                        <li><a class="dropdown-item" href="#" @click="changeButtonColor('Gray','btn-secondary')">Gray</a></li>
                    </ul>
                </div>
                

            </div>

            <div class="row g-0 p-0   d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 " style="transform: translate(0,3px);">Outline button</p>
                <button @click="toggleOutline" class="btn btn-sm col-6 p-1 m-0" >toggle Outline</button>
            </div>
    </div>

</template>

<script>
export default {
    data(){
        return{
            buttonSize: "small" ,
            buttonColor: "Blue" ,
        }
    },
    methods:{
        changeButtonSize(s){
            this.buttonSize = s ;
            if (s === 'Small')
                this.$emit('changeButtonSize','btn-sm');
            else if(s === 'Large')
                this.$emit('changeButtonSize','btn-lg');
            else 
                this.$emit('changeButtonSize','');
        },
        changeButtonColor(clr,btsClr){
            this.buttonColor = clr ;
            this.$emit('changeButtonColor',btsClr) ;
        },
        toggleOutline(){
            this.$emit('toggleOutline') ;
        }
        
    }
}
</script>

<style scoped>
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