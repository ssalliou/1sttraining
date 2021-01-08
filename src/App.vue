<template>
  <div id="app">
    <Nav class="mb-4" />
    <Employees />
    <Footer class="mb-4"/>
  </div>
</template>

<script>
import Nav from "./components/Nav";
import Employees from "./components/Employees";
import Footer from "./components/Footer";

export default {
  name: "app",
  components: {
    Nav,
    Employees,
    Footer
  }
};
</script>

<style></style>
