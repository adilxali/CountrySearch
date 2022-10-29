<script setup>
import { onMounted, ref, watchEffect, computed } from "vue";
import Data from "../components/Data.vue";

const news = ref([]);
const search = ref("");
const error = ref(false);
const serachSomething=ref("Please Search Something")

// https://newsapi.org/v2/everything?q=${title}&apiKey=7e66c8c2e4954514b8ac54efcf72bd7d

const getNews = async (title) => {
  await fetch(`https://restcountries.com/v3.1/all/${title}`)
    .then((res) => res.json())
    .then((data) => (news.value = data))
    .catch((err) => (error.value = err));
};
const searchfilterData = computed(() => {
  //  return search.value !== '' ? news.value.filter( ({name})=> name.common === search.value) : "No data";

  if (!search.value) {
    return ;
  } else {
    return news.value.filter((item) =>
      item.name.common.toLowerCase().includes(search.value.toLowerCase())
    );
  }
});
onMounted(() => {
  getNews(search.value);
});
watchEffect(() => {
  console.log("news.value", news.value);
  console.log("searchfilterData", searchfilterData.value);
});
</script>

<template>
  <div>
    <input type="text" v-model="search" placeholder="Entery Country Name" />
    <div v-if="error">opps {{ error.message }}</div>

    <!-- <div v-for="(value, index) in searchfilterData" :key="index">
          {{ value.name }}
        </div> -->
    <Data :item="searchfilterData" />
  </div>
</template>
<style scoped>
input {
  width: 50%;
  height: 50px;
  left: 50%;
  right: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;
}
</style>
