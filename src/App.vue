<template>
  <div id="app">
    <Form />
  </div>
</template>

<script>
import Form from "@/components/Form";

export default {
  name: "App",
  components: { Form }
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  list-style: none;
  outline: none;
  box-sizing: border-box;
}

#app {
  @import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");
  font-family: "Roboto", sans-serif;
  background-color: #ffdf8c;
  font-size: 14px;
}
</style>
