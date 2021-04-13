<template>
  <div class="home">
    <div class="brand">
      <img src="../assets/images/Grupo 19.svg">
    </div>
    <section class="container">
      <Form/>
    </section>
  </div>
</template>
<script>
import Form from "../components/Form.vue";

export default {
  name: "Home",
  components: { Form }
};
</script>

<style lang="scss">
@import "../assets/scss/generic/colors";

.home {
  display: grid;
  grid-template-rows: 400px 1fr;
  background-image: url("../assets/images/Grupo 2.png");
  background-position: center;
  width: 100vw;
  height: 100vh;

  @media only screen and (min-width: 764px) {
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    height: 100vh;
  }

  > .banner {
    width: 100vw;
    height: 100vh;
    object-fit: cover;
  }
  > .brand {
    color: white;
    text-align: end;
    grid-row-start: 2;

    @media only screen and (min-width: 764px) {
      position: relative;
      left: 300px;
    }
  }

  > .container {
    color: white;
    background-color: $secondary;
    grid-row-start: 3;
    max-height: 100%;
    padding-bottom: 20px;

    @media only screen and (min-width: 764px) {
      max-height: 80vh;
      margin-right: auto;
      margin-left: auto;
      background-color: rgba(143, 140, 140, 0.5);
      border-radius: 10px;
      backdrop-filter: blur(5px);
      padding-bottom: 0px;
    }
  }
}
</style>
