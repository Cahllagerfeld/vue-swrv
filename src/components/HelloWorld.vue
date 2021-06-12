<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import useSWRV from "swrv";
import axios from "axios";
import { IResponse } from "swrv/dist/types";

@Component({
  props: {
    msg: String,
  },
  setup() {
    const fetcher = () => {
      return axios.get("https://jsonplaceholder.typicode.com/users");
    };

    const { data }: IResponse = useSWRV("/todos", fetcher);

    return {};
  },
})
export default class HelloWorld extends Vue {}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
