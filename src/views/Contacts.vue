<template>
  <div class="contacts">
    <div class="appBar">
      <img src="../assets/images/Grupo 19.svg" class="logo">
    </div>
    <div class="content">
      <List/>
    </div>

    <div class="register">
      <button class="btn-register" @click="registerPageHandler">CADASTRAR</button>
    </div>
  </div>
</template>

<script>
import List from "../components/List.vue";
export default {
  name: "Contacts",

  components: { List },

  methods: {
    registerPageHandler() {
      this.$router.push("/");
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/generic/colors";

.contacts {
  > .appBar {
    height: 100px;
    background: $secondary;

    display: flex;
    align-items: center;

    > .logo {
      height: 71px;
      padding-left: 30px;
      @media only screen and (min-width: 764px) {
        padding-left: 100px;
      }
    }
  }

  > .content {
    display: flex;
    justify-content: center;
    align-items: center;
    height: calc(100vh - 71px);
    overflow-x: auto;
  }
  > .register {
    display: flex;
    justify-content: center;
    padding-bottom: 50px;
    > .btn-register {
      height: 72px;
      border-radius: 9px;
      background: $primary;
      color: white;
      width: 409px;
      cursor: pointer;

      &:hover {
        opacity: 0.9;
      }
    }
  }
}
</style>
