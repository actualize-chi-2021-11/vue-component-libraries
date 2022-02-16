<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>Example chart</h2>
    <line-chart :data="{ '2017-05-13': 2, '2017-05-14': 5 }"></line-chart>
    <pie-chart
      :data="[
        ['Blueberry', 44],
        ['Strawberry', 23],
      ]"
    ></pie-chart>
  </div>
</template>
