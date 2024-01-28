<template>
  <div class="content-wrapper">
    <div class="fields">
      <div v-for="f of dynamicFields">
        <DynamicInput v-if="['text', 'int', 'password'].includes(f.type)" :name="f.name" :type="f.type"></DynamicInput>
        <Cards v-else-if="f.type === 'card'" :dataUri="f.dataUri"></Cards>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
let dynamicFields: any[] = [
  // {
  //   id: 1,
  //   type: "text",
  //   name: "Campo de Texto",
  // },
  // {
  //   id: 2,
  //   type: "int",
  //   name: "Campo de Inteiro",
  // },
  // {
  //   id: 3,
  //   type: "password",
  //   name: "Campo de Password",
  // },
  // {
  //   id: 4,
  //   type: "card",
  //   name: "Campo de Texto",
  //   dataUri: "https://masterlink-mock-api.mwe.pt/MlkApi/bpm_data/1,f4",
  // }
];

const { data: fetchData }: any = await useFetch("https://masterlink-mock-api.mwe.pt/MlkApi/bpm_metadata/1");
if (fetchData.value) dynamicFields = fetchData.value.fields;
</script>

<style>
* {
  font-family: Verdana, sans-serif;
}

.content-wrapper {
  min-width: 300px;
  max-width: 1500px;
  width: 70vw;
  margin-inline: auto;
  margin-top: 4rem;
  padding: 2rem;
  border: 2px solid #222;
  border-radius: 20px;
}

.fields {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>