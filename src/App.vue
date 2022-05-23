<template>
<div class="container m-0 p-0" ref="container" >
    <div class="row">
      <div class="col-9 d-flex ms-5 mt-5 justify-content-center align-items-center" id="main">
        <PrincingCard class=""></PrincingCard>

      </div>
      <div  class="col-3 hide p-0" style="overflow-y : auto;" >
        <ControlText></ControlText>
      </div>
    </div>
</div>
</template>

<script>
import PrincingCard from './components/princingCard.vue';
import ControlText from './components/ControlText.vue';

export default {
  name: 'App',
  components: {
    PrincingCard,
    ControlText
}
}
</script>

<style>
.col-3{
    position: fixed;
    max-width : 290px !important;
    right: 0;
    height: 100vh;
    background : #3e3e46;
}
</style>
