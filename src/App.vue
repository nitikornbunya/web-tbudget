<template>
  <div id="app">
    <div class="button-area">
      <v-btn
        color="blue-grey"
        class="ma-2 white--text"
        @click="pageNumber = pageNumber - 1"
      >
        <v-icon right dark> mdi-arrow-left </v-icon>
        Previous
      </v-btn>
      <!-- <h2>{{ pageNumber }}</h2> -->
      <v-col cols="12" sm="6" md="3">
        <v-text-field
          label="Solo"
          placeholder="Placeholder"
          solo
          type="number"
          v-model="pageNumber"
        ></v-text-field>
      </v-col>
      <v-btn
        color="blue-grey"
        class="ma-2 white--text"
        @click="pageNumber = Number(pageNumber) + 1"
      >
        Next
        <v-icon right dark> mdi-arrow-right </v-icon>
      </v-btn>
    </div>
    <div
      v-for="(item, index) in dataJson['2022.3.1'][Number(pageNumber) + 21]"
      :key="index"
    >
      <div v-if="index !== 0">
        <span
          :title="'left: ' + item.coordinate[0].x + ', top: ' + item.coordinate[3].y"
          v-bind:style="{
            left: item.coordinate[0].x + 'px',
            top: item.coordinate[3].y + 'px',
            position: 'absolute',
          }"
        >
          {{ item.text }}
        </span>
        <!-- <span title="I am hovering over the text">This is the text I want to have a mousover</span> -->
      </div>
    </div>
  </div>
</template>

<script>
import dataJson from "@/assets/2022-3-1.json";

export default {
  name: "App",
  data: function () {
    return {
      dataJson: dataJson,
      pageNumber: 0,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
.button-area {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
.v-text-field__details {
  display: none !important;
}
</style>
