<template>
<div class="container m-0 p-0" ref="container" >
    <b-row >
      <b-col cols="9"  class="d-flex ms-5 mt-5" id="main">
        <PrincingCard class=""></PrincingCard>
        <PrincingCard class=""></PrincingCard>
        <PrincingCard class=""></PrincingCard>
      </b-col>
      <b-col cols="3"  class="hide p-0" style="overflow-y : auto;" >
        <ControlText></ControlText>
      </b-col>
    </b-row>
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
