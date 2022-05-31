<template>

<div class="container-fluid m-0 p-0 d-flex " ref="container" >
      <div class="ma d-flex justify-content-center align-items-center pricing-cards h-auto" id="main" ref="heightSelector">
          <div id="widthSelector" ref="widthSelector" class="w-100">
        <PrincingCard v-for="box in boxes" :key="box.id" @focus="handleFocus($event,box.id)" :active="box.active" @handleText="handleText" :buttonSize="box.buttonSize" :buttonColor="box.buttonColor" :showButton="box.showButton" :border="box.border" :corner="box.corner"  :shadow="box.shadow" >
        <svg v-if="box.active" style="cursor:pointer;" @click="deleteBox" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="black" class="bi bi-trash-fill position-absolute top-0 end-50" viewBox="0 0 16 16">
  <path d="M2.5 1a1 1 0 0 0-1 1v1a1 1 0 0 0 1 1H3v9a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V4h.5a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1H10a1 1 0 0 0-1-1H7a1 1 0 0 0-1 1H2.5zm3 4a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 .5-.5zM8 5a.5.5 0 0 1 .5.5v7a.5.5 0 0 1-1 0v-7A.5.5 0 0 1 8 5zm3 .5v7a.5.5 0 0 1-1 0v-7a.5.5 0 0 1 1 0z"/>
</svg>
        </PrincingCard>
      
      </div>
      </div>
      <div  class="hide control " style="overflow-y : auto;" >
      <ControlBoxes @changeCardWidth="changeCardWidth" @handleMouseLeave="handleMouseLeave"  @ListNum="ListNum" @uploadImgBackground="uploadImgBackground" @changeBackground="changeBackground" @changeCardHeight="changeCardHeight" :length="boxes.length"></ControlBoxes>
      <ControlBox v-if="focusOn != null" @changeBoxBackground="changeBoxBackground" @handleCardButton="handleCardButton" @handleBorder="handleBorder" @handleBorderStyle="handleBorderStyle" :boxes="boxes" :focusOn="focusOn" @handleShadow="handleShadow" @handleShadowBtn="handleShadowBtn"></ControlBox>
      <ControlButton v-if="focusOn != null" @changeButtonSize="changeButtonSize"  @changeButtonColor="changeButtonColor" @toggleOutline="toggleOutline" />
      <ControlText v-if="showControlText" @changeWeight="changeWeight" @changetextColor="changetextColor" @changeTextSize="changeTextSize" @changeFontSize="changeFontSize"></ControlText>
      </div>

</div>
</template>

<script>
import PrincingCard from './components/princingCard.vue';
import ControlText from './components/ControlText.vue';
import ControlBoxes from './components/ControlBoxes.vue';
import ControlBox from './components/ControlBox.vue';
import ControlButton from './components/ControlButton.vue';

export default {
  name: 'App',
  components: {
    PrincingCard,
    ControlText,
    ControlBoxes,
    ControlButton,
    ControlBox
},
  data(){
    return {
        boxInfo : {
          top : null,
          bottom : null
        },
        focusOn : null,
        counter : 3,
        selectedText : null,
        showControlText : false,
        previousClass : 'w-100',
      boxes : [
        { id : 0 ,active : false,buttonSize : '', buttonColor : 'btn-dark', showButton : true ,
        shadow : {
        active : false,
        offset : {x : 0 , y : 0},
        blur : 0,
        spread : 0,
        color : "#000000"
      },corner : 0,
        bgColor : "#000000",
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },},
        { id : 1,active : false, buttonSize : '' , buttonColor : 'btn-dark',showButton : true,shadow : {
        active : false,
        offset : {x : 0 , y : 0},
        blur : 0,
        spread : 0,
        color : "#000000"
      },corner : 0,
        bgColor : "#000000",
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },},
        {id : 2,active : false , buttonSize : ''  ,buttonColor : 'btn-dark',showButton : true,shadow : {
        active : false,
        offset : {x : 0 , y : 0},
        blur : 0,
        spread : 0,
        color : "#000000"
      },corner : 0,
        bgColor : "#000000",
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },},
      ] 
    }
  },
  
  methods : {
    handleActiveBox(id){
        this.boxes.map(box=>{
           if(box.id === id) box.active = true
          else box.active = false
        })

    },
    handleFocus(info,id){
        this.focusOn = id
        this.boxInfo = info
        this.handleActiveBox(id)

    },
    handleText(target){
      this.showControlText = true ;
      this.selectedText = target
    },
    changeCardWidth(width,e){
      if(e.type === 'mouseenter'){
          this.hover = true
      if(width === 'small'){

        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add("w-50");
      }
      if(width === 'medium'){
        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add("w-75");

      }
      if(width === 'big'){
        this.$refs.widthSelector.className = '';
        this.$refs.widthSelector.classList.add('w-100')
      }
      }

      else if (e.type == 'click') {
        this.previousClass = this.$refs.widthSelector.className
        this.hover = false
      }
      
      },
      handleMouseLeave(e){
          if(this.hover){
              this.$refs.widthSelector.className = '';
              this.$refs.widthSelector.classList.add(this.previousClass)
          }
          this.hover = false
      },
      changeCardHeight(height){
        const lastClass = this.$refs.heightSelector.classList.value.split(' ').pop()
        this.$refs.heightSelector.classList.remove(lastClass)
        this.$refs.heightSelector.classList.add(height)

      },
    changeTextSize(cls){
      this.selectedText.style.fontSize = ''
      this.selectedText.className = '';
      if ( cls !== 'n')
      this.selectedText.classList.add(cls);
      console.log(this.selectedText.classList)

    },
    changeFontSize(fs){
       this.selectedText.style.fontSize = fs ;
    },
    changeWeight(cls){
       this.selectedText.classList.toggle(cls)
    },
    changetextColor(clr){
       this.selectedText.style.color = clr ;
    },
    uploadImgBackground(e){
      const image = e.target.files[0] ;    
      document.body.style.backgroundImage = 'url(' + window.URL.createObjectURL(image) + ')' ;
      e.target.value = '' ;
    },
    changeBackground(color){
      document.body.style.background = color
    },
    deleteBox(){
     this.boxes = this.boxes.filter(box => box.id != this.focusOn)
     this.handleFocus(null)
      this.showControlText = null
    },
    ListNum(num){
      while (num !== this.boxes.length){
        if (num > this.boxes.length)
        {
          this.boxes.push( { id : this.counter++,active : false,buttonSize : '', buttonColor : 'btn-dark', showButton : true,shadow : {
        active : false,
        offset : {x : 0 , y : 0},
        blur : 0,
        spread : 0,
        color : "#000000"
      },corner : 0,
      bgColor : "#000000",
      border : {
          width : 0,
          radius : 0,
          color : "#000000",
          style : "solid"
      },} )
            // is set ??
        }else{
          this.boxes.pop()
        }
      }
    },
      changeButtonSize(size){
        this.boxes.map(box =>{
          if(box.id === this.focusOn) box.buttonSize = size ;
        }) 
      },
      changeButtonColor(clr){
        this.boxes.map(box =>{
          if(box.id === this.focusOn) box.buttonColor = clr ;
        })        
      },
      toggleOutline(){
        this.boxes.map(box =>{
          if(box.id === this.focusOn){
            if (!box.buttonColor.includes('outline')){
              const  newColor = 'btn-outline' + box.buttonColor.substring(3, box.buttonColor.length) ;
              box.buttonColor = newColor ;
            }else {
              const newColor =  'btn-' + box.buttonColor.substring(12, box.buttonColor.length) ;
              box.buttonColor = newColor ;
            }
          }
        })  
      },
      changeBoxBackground(color){
        this.boxInfo.top.style.backgroundColor = color
        this.boxInfo.bottom.style.backgroundColor = color
        this.boxes.map(box=> {
          if(box.id === this.focusOn) {
            box.bgColor = color
            return
          }
        })

      },
      handleCardButton(action){
          this.boxes.map(box =>{
          if(box.id == this.focusOn) {
          if(action === 'del') box.showButton = false
          else box.showButton = true
          return
        }
      })
      },
      handleBorder(c,type){
        this.boxes.map(card => {
          if(card.id === this.focusOn){
                      if(type == 'width')
                      card.border.width = c
                      else if(type == 'color')
                      card.border.color = c
                      else
                      card.border.radius = c
  
          }
        })

      },
      handleBorderStyle(style){
        this.boxes.map(card =>{
          if(card.id === this.focusOn) card.border.style = style
        })
      },
      handleShadow(value,option){
         this.boxes.map(card=>{
          if(card.id===this.focusOn) {
            if(option==='x') card.shadow.offset.x = value
            else if(option==='y') card.shadow.offset.y = value
            else if(option==='color') card.shadow.color = value
            else if(option==='blur') card.shadow.blur = value
            else card.shadow.spread = value
          }
        })
      },
        handleShadowBtn(value){
        this.boxes.map(box=>{
          if(box.id===this.focusOn) {
            box.shadow.active = value
            box.shadow.offset.x = 0
            box.shadow.offset.y = 0
            box.shadow.color = '#000000'
            box.shadow.spread = 0
            box.shadow.blur = 0
          }
        })
      },
    
  },
    mounted(){
        document.body.addEventListener("click",(e)=>{
          if(e.altKey){
            this.handleFocus(null)
            this.showControlText = null
            
          }
        })
    },

}
</script>

<style scoped>
.control{
  width : 290px !important;
    position: fixed;
    right: 0;
    height: 100vh;
    background : #3e3e46;
}
.pricing-cards{
  padding: 1em;
  padding-top : 2em;
}
@media only screen and (max-width: 970px) {
  #widthSelector {
    flex-wrap : wrap;
     width : 70% !important;}
  .hide 
  {
    display: none;
  }
  #main{
    margin:auto
  }
  .pricing-cards{
    width: 100% ;
  }
}
#widthSelector{
  display: flex;
  justify-content: center;
}
@media only screen and (min-width: 970px) {
  .pricing-cards{
    width: calc(100% - 290px);
  }
}
</style>
