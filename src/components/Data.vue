<script setup>
import { ref } from "vue";
const props = defineProps({
  item: [],
});
const detail = ref(false);
</script>
<template>
  <div
    class="col-sm-10  mx-auto mb-1   card text-center text-dark"
    v-for="(value, index) in item"
    :key="index"
  >
  <h3 class="card-title text-dark fs-1">{{ value.name.common }} <img :src="value.flags.png" alt="flag" class="flag"/></h3>
    <div class="card d-flex flex-row ">
    <div class=" col-sm-4 card-body  border border-end-3 text-start">
      
      
      <p class="card-text"><b>Official Name</b> : {{ value.name.official }}</p>
      <p class="carr-text" ><b>Capital :</b> <span v-for="(cap,index) in value.capital">{{ cap }} <br/></span></p>
      <p class="carr-text"><b>Region :</b> {{ value.region }}</p>
      <p class="carr-text"><b>Population :</b> {{ value.population }}</p>
      <p class="carr-text"><b>Time-Zone :</b> <span v-for="(tzone, index) in value.timezones">&nbsp; {{ tzone }}</span></p>
      
    </div>
    <div class="col-sm-3 card-body text-start">
    <p class="carr-text"><b>Language :</b> <span v-for="(lang,index) in value.languages"> &nbsp;{{lang}} </span></p>
    <p class="carr-text"><b>Currance :</b> <span v-for="(curr,index) in value.currencies"> &nbsp;{{curr.name}} </span></p>
    <p class="carr-text"><b>Independent :</b> <span > &nbsp;{{value.independent}} </span></p>
    <p class="carr-text"><b>UN MemberShip :</b> <span > &nbsp;{{value.unMember}} </span></p>
    </div>
    </div>
  </div>
</template>
<style setup>
.flag{
    /* width: 16px; */
    height: 25px;
}</style>
