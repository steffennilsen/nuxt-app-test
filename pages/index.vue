<script setup>
const { data } = await useFetch('/api/tickers?limit=10');
console.log('1] data', data);

if (data.value) {
  console.log('2] data.value', data.value);
}

if (data.value.data) {
  console.log('3] data.value.data', data.value.data);
}

if (data.data) {
  console.log('2] data.data', data.data);
}
</script>

<template>
  <main>
    <h1>Index Page</h1>

    <table border="1 px solid">
      <thead>
        <tr>
          <th>Name</th>
          <th>Symbol</th>
          <th>Price</th>
          <th>Details</th>
        </tr>
      </thead>
      <tr v-for="currency in data.data" :key="data.id">
        <td>{{ currency.name }}</td>
        <td>{{ currency.symbol }}</td>
        <td>{{ currency.price_usd }}</td>
        <td>
          <NuxtLink :to="'/currency/' + currency.id">{{
            currency.id
          }}</NuxtLink>
        </td>
      </tr>
    </table>
  </main>
</template>
