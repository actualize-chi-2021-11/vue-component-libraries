<script>
import VueMultiselect from "vue-multiselect";
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

import "v-calendar/dist/style.css";
import { Calendar, DatePicker } from "v-calendar";

import { VueDraggableNext } from "vue-draggable-next";

export default {
  components: {
    Calendar,
    DatePicker,
    VueMultiselect,
    Carousel,
    Slide,
    Pagination,
    Navigation,
    draggable: VueDraggableNext,
  },
  data() {
    return {
      selected: null,
      options: ["list", "of", "options"],
      date: new Date(),
      images: [
        "https://ichef.bbci.co.uk/news/999/cpsprodpb/15951/production/_117310488_16.jpg",
        "https://media.istockphoto.com/photos/hot-air-balloons-flying-over-the-botan-canyon-in-turkey-picture-id1297349747?b=1&k=20&m=1297349747&s=170667a&w=0&h=oH31fJty_4xWl_JQ4OIQWZKP8C6ji9Mz7L4XmEnbqRU=",
      ],
      enabled: true,
      list: [
        { name: "John", id: 1 },
        { name: "Joao", id: 2 },
        { name: "Jean", id: 3 },
        { name: "Gerard", id: 4 },
      ],
      dragging: false,
    };
  },
  methods: {
    log(event) {
      console.log(event);
    },
  },
};
</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h2>Example draggable</h2>
    <draggable class="dragArea list-group w-full" :list="list" @change="log">
      <div
        class="list-group-item bg-gray-300 m-1 p-3 rounded-md text-center"
        v-for="element in list"
        :key="element.name"
      >
        {{ element.name }}
      </div>
    </draggable>

    <h2>Example calendar</h2>
    <Calendar />

    <h2>Example datepicker</h2>
    <DatePicker v-model="date"></DatePicker>
    <p>You selected {{ date }}</p>

    <h2>Example carousel</h2>
    <Carousel>
      <Slide v-for="image in images" :key="image">
        <div class="carousel__item">
          <img :src="image" alt="" />
        </div>
      </Slide>

      <template #addons>
        <Navigation />
        <Pagination />
      </template>
    </Carousel>

    <Carousel :itemsToShow="3.95" :wrapAround="true">
      <Slide v-for="slide in 10" :key="slide">
        <div class="carousel__item">{{ slide }}</div>
      </Slide>

      <template #addons>
        <Pagination />
      </template>
    </Carousel>

    <h2>Example multi-select</h2>
    <VueMultiselect v-model="selected" :multiple="true" :options="options"></VueMultiselect>
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

<style src="vue-multiselect/dist/vue-multiselect.css"></style>
<style>
.carousel__item {
  height: 200px;
  width: 100%;
  background-color: var(--vc-clr-primary);
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel__item img {
  width: 100%;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid white;
}

.carousel__slide > .carousel__item {
  transform: scale(1);
  opacity: 0.5;
  transition: 0.5s;
}
.carousel__slide--visible > .carousel__item {
  opacity: 1;
  transform: rotateY(0);
}
.carousel__slide--next > .carousel__item {
  transform: scale(0.9) translate(-10px);
}
.carousel__slide--prev > .carousel__item {
  transform: scale(0.9) translate(10px);
}
.carousel__slide--active > .carousel__item {
  transform: scale(1.1);
}
</style>
