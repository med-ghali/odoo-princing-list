<template>
<div class="container-fluid m-0 p-0 d-flex " ref="container" >

      <div class=" d-flex justify-content-center align-items-center pricing-cards" id="main" >
        <PrincingCard v-for="box in boxes" :key="box.id" @focus="handleFocus(box.id)" :active="box.active" @handleText="handleText"></PrincingCard>
      </div>
      <div  class="hide col-3 " style="overflow-y : auto;" >
      <ControlBoxes @uploadImgBackground="uploadImgBackground" @changeBackground="changeBackground"></ControlBoxes>
        <ControlText v-if="showControlText" @changeWeight="changeWeight" @changetextColor="changetextColor" @changeTextSize="changeTextSize" @changeFontSize="changeFontSize"></ControlText>
      </div>

</div>
</template>

<script>
import PrincingCard from './components/princingCard.vue';
import ControlText from './components/ControlText.vue';
import ControlBoxes from './components/ControlBoxes.vue';

export default {
  name: 'App',
  components: {
    PrincingCard,
    ControlText,
    ControlBoxes
},
  data(){
    return {
        focusOn : null,
        counter : 3,
        selectedText : null,
        showControlText : false,
      boxes : [
        { id : 0 ,active : false},
        { id : 1,active : false},
        {id : 2,active : false},
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
    handleFocus(id){
        this.focusOn = id
        this.handleActiveBox(id)

    },
    handleText(target){
      this.showControlText = true ;
      this.selectedText = target
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
.col-3{
    position: fixed;
    width : 290px !important;
    right: 0;
    height: 100vh;
    background : #3e3e46;
}
.pricing-cards{
  width: calc(100% - 290px);
  padding: 1em;
  padding-top : 2em;
}
</style>
