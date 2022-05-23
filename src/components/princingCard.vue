<template>
  <div class="card p-0 m-2 " @click="focus" :class="{outsideBorder:active}">
        <div class="inner-div ">
        <div class="card-header text-center bg-primary p-3">
            <h4  contenteditable="true" @dblclick="handleText" style="min-height: 90px; line-height: 90px;">Beginner</h4>
        </div>
        <div class="card-body text-center p-0">
            <h1 class="bg-light mx-0 p-5" contenteditable="true" @dblclick="handleText">  $15 <small>/mo</small></h1>
            <ul class="list-group list-group-flush">
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">An item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A second item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A third item</li>
                <li class="list-group-item" contenteditable="true" @dblclick="handleText">A fourth item</li>
            </ul>
        </div>
        <div class="card-footer text-muted text-center">
            <p contenteditable="true" @dblclick="handleText"> Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequatur, dicta!</p>
            <button class="btn btn-primary " contenteditable="true" @dblclick="handleText"> Lorem, ipsum.</button>
        </div>
        </div>
  </div>
</template>

<script>
export default {
    props : ['active'],
    
    methods : {

        focus(){
            this.$emit('focus')
        },
        handleText(e){
            this.$emit('handleText',e.target)
        }
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
}

</style>