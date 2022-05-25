<template>
  <div class="card p-0 m-2 w-100 " @click="focus" :class="{outsideBorder:active}"  style="overflow: hidden;">
        <slot class="trash-icon"></slot>
        <div class="inner-div " ref="borderSelector">
        <div class="card-header text-center  p-3" style="background : #212529" ref="top">
            <h4  contenteditable="true"  @dblclick="handleText" style="color : white;">Beginner</h4>
        </div>
        <div class="card-body text-center p-0">
            <h1 class="bg-light mx-0 py-5" style="min-height: 75px; line-height: 75px;" contenteditable="true" @dblclick="handleText">  $15 <small>/mo</small></h1>
            <ul class="list-group list-group-flush">
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">An item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A second item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A third item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A fourth item</li>
            </ul>
        </div>
        <div class="card-footer text-muted text-center" ref="bottom">
            <p contenteditable="true" @dblclick="handleText"> Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequatur, dicta!</p>
            <button v-if="showButton" :class="[buttonSize,buttonColor]" class="btn"  @dblclick="handleText"> Lorem, ipsum.</button>
        </div>
        </div>
  </div>
</template>

<script>
export default {
    props : ['active','buttonSize','buttonColor','showButton','border','corner','shadow'],
    
    methods : {

        focus(){
            this.$emit('focus',{top :this.$refs.top, bottom : this.$refs.bottom})
        },
        handleText(e){
            this.$emit('handleText',e.target)
        },
        handleBorder(){
            const b= this.border.width+"px "+this.border.style+" "+this.border.color
            this.$refs.borderSelector.style.border = b
            this.$refs.borderSelector.style.borderRadius = this.border.radius+"px"
        },
        handleShadow(){
            const s = this.shadow.offset.x+"px "+this.shadow.offset.y+"px "+this.shadow.blur+"px "+this.shadow.spread+"px "+this.shadow.color
            this.$refs.borderSelector.style.boxShadow = s
        }
    },
    watch : {
        'border.width' : function(){
            this.handleBorder()
        },
        'border.radius' : function(){
            this.handleBorder()
        },
        'border.color' : function(){
            this.handleBorder()
        },
        'border.style' : function(){
            this.handleBorder()
        },
        'shadow.color' : function(){
            this.handleShadow()
        },
        'shadow.blur' : function(){
            this.handleShadow()
        },
        'shadow.spread' : function(){
            this.handleShadow()
        },
        'shadow.offset.x' : function(){
            this.handleShadow()
        },
        'shadow.offset.y' : function(){
            this.handleShadow()
        },
    }
}
</script>

<style scoped>
*{
    outline : none;
}
.outsideBorder{
  padding : 1em !important;
    border : 2px solid #01bad2;
    position: relative;
}


</style>