<template>
  <div class="cardWrapper">
    <div class="card" v-for="c of cards" :style="{ width: 95 / cards.length + '%' }">
      <img :src="c.imageUri" />
      <a :href="c.link">{{ c.text }}</a>
    </div>
  </div>
</template>

<script setup lang="ts">
let cards: any[] = [];
const props = defineProps(["dataUri"]);
const { data: cardsFetchData }: any = await useFetch(props.dataUri);
if (cardsFetchData.value) cards = cardsFetchData.value.data;
// cards = [
// {
//   imageUri:
//     "https://www.google.com/logos/doodles/2023/seasonal-holidays-2023-6753651837110165.2-6752733080612634-cst.gif",
//   text: "Pesquise com a Google",
//   link: "http://www.google.com",
// },
// {
//   imageUri: "https://th.bing.com/th/id/OIP.5NOQA54z4ElAw4E33TDLVQHaE8?w=239&h=180&c=7&r=0&o=5&pid=1.7",
//   text: "Pesquise com o Bing",
//   link: "http://www.bing.com",
// },
// {
//   imageUri:
//     "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Yahoo%21_%282019%29.svg/800px-Yahoo%21_%282019%29.svg.png?20190923130707",
//   text: "Pesquise com o Yahoo!",
//   link: "http://www.yahoo.com",
// },
// ];
</script>

<style>
.cardWrapper {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.card {
  box-sizing: border-box;
  height: 150px;
  min-width: 205px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 1px solid #ffa51f;
  position: relative;
}

.card img {
  max-width: 90%;
  max-height: 100px;
}

.card a {
  box-sizing: border-box;
  text-decoration: none;
  color: #222;
  font-weight: 400;
  cursor: pointer;
  transition: transform 300ms ease-in-out;
  width: 90%;
  font-size: 80%;
  text-align: center;
  position: absolute;
  bottom: 5%;
}

.card a:hover {
  transform: scale(1.05);
}
</style>
