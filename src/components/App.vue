<template>
  <div>
    <component :is="currentComponent"></component>
  </div>
</template>
<script>
import component from "./component.vue";
import axios from "axios";
import { ref } from "vue";
export default {
  setup() {
    const result = ref(null);

    axios
      .get("https://icanhazdadjoke.com/")
      .then((data) => (result.value = data));

    return { result };
  },

  components: {
    component,
  },
  data() {
    return {
      currentComponent: "component",
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Sen&display=swap");

body {
  font-family: "Sen", sans-serif;
  background-color: hsl(218, 23%, 16%);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background-color: hsl(217, 19%, 24%);
  text-align: center;
  padding: 10px;
  max-width: 400px;
  color: hsl(193, 38%, 86%);
  position: relative;
}

h1 {
  font-size: 25px;
  color: hsl(150, 100%, 66%);
}
p {
  margin-bottom: 30px;
  font-size: 20px;
}

button {
  background-color: hsl(150, 100%, 66%);
  border: none;
  font-family: inherit;
  padding: 10px 30px;
  font-size: 17px;
  border-radius: 15px;
  position: relative;
  position: absolute;
  top: 93%;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer;
}

button:hover {
  transition: ease-in-out 0.3s;
  -webkit-box-shadow: 0px 3px 39px 4px rgba(81, 255, 168, 1);
  -moz-box-shadow: 0px 3px 39px 4px rgba(81, 255, 168, 1);
  box-shadow: 0px 3px 39px 4px rgba(81, 255, 168, 1);
}
</style>
