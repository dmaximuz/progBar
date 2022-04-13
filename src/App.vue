<template>
  <div id="app" class="h-screen">
    <h2 class="ml-6 pt-3 text-lg font-semibold">Colors</h2>
    <div class="flex flex-wrap p-4">
      <base-progress
        v-for="(color, index) in colors"
        :color="color"
        :percentage="progressStart + index * 10"
        :key="color"
        class="mx-2 mb-2"
      />
    </div>
    <h2 class="ml-6 pt-3 text-lg font-semibold">Sizes</h2>
    <div class="flex flex-wrap p-4">
      <base-progress :percentage="20" class="mx-2 mb-2"/>
      <base-progress :percentage="40" class="mx-2 mb-2 h-3"/>
      <base-progress :percentage="60" class="mx-2 mb-2 h-4"/>
      <base-progress :percentage="80" class="mx-2 mb-2 h-6"/>
    </div>
    <h2 class="ml-6 pt-3 text-lg font-semibold">Content</h2>
    <div class="flex flex-wrap p-4">
      <base-progress :percentage="contentProgress" class="mx-2 mb-2 h-5">
        <span class="text-xs text-white w-full flex justify-end pr-2">{{contentProgress}}%</span>
      </base-progress>
      <div class="ml-2 mt-1 flex">
        <button
          @click="decreasePercentage"
          class="px-4 border text-xl border-teal-600 border-r-0 text-teal-600 hover:bg-teal-600 hover:text-white rounded-l focus:outline-none focus:shadow-outline"
        >-</button>
        <button
          @click="increasePercentage"
          class="px-4 border text-xl border-teal-600 text-teal-600 hover:bg-teal-600 hover:text-white rounded-r focus:outline-none focus:shadow-outline"
        >+</button>
      </div>
    </div>
    <h2 class="ml-6 pt-3 text-lg font-semibold">Indeterminate</h2>
    <div class="flex flex-wrap p-4">
      <base-progress :percentage="contentProgress" class="mx-2 mb-2" indeterminate></base-progress>
    </div>
  </div>
</template>

<script>
import BaseProgress from "./components/BaseProgress";

export default {
  name: "App",
  components: {
    BaseProgress
  },
  data() {
    return {
      colors: [
        "gray",
        "yellow",
        "orange",
        "red",
        "green",
        "teal",
        "blue",
        "indigo",
        "purple",
        "pink"
      ],
      progressStart: 10,
      contentProgress: 20
    };
  },
  methods: {
    increasePercentage() {
      if (this.contentProgress <= 80) {
        this.contentProgress += 20;
      }
    },
    decreasePercentage() {
      if (this.contentProgress >= 20) {
        this.contentProgress -= 20;
      }
    }
  }
};
</script>

<style>
</style>
