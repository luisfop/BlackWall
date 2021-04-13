<template>
  <div class="form-sign">
    <h4 class="title">Lista de Espera</h4>
    <form class="form">
      <div class="sub-group">
        <div class="ddd">
          <label>DDD</label>
          <input type="number" class="input" required placeholder="11" v-model="form.ddd">
        </div>

        <div class="sub-input-group">
          <label>Telefone</label>
          <input
            class="input"
            type="number"
            required
            v-model="form.telefone"
          >
        </div>
      </div>

      <div class="input-group">
        <label for="telefone">Tipo de Telefone</label>
        <select name="tel-option" class="input select" v-model="form.phoneType" required>
          <option value="Celular">Celular</option>
          <option value="Trabalho">Trabalho</option>
          <option value="Residencial">Residencial</option>
        </select>
      </div>

      <div class="input-group radio">
        <input
          type="radio"
          class="item"
          name="phone"
          v-model="form.isActive"
          :value="'Ativo'"
          required
        >
        <label for="male">Telefone Ativo</label>

        <input
          type="radio"
          class="item"
          name="phoneInactive"
          v-model="form.isActive"
          :value="'Inativo'"
          required
        >
        <label for="female">Telefone Inativo</label>
      </div>

      <div class="input-group">
        <label>Nome</label>
        <input type="text" class="input" required v-model="form.nome">
      </div>

      <div class="input-group">
        <label>Sobrenome</label>
        <input type="text" class="input" required v-model="form.sobrenome">
      </div>
      <button class="btn btn-add" @click="handleRegister">Adicionar</button>
      <button class="btn table" @click="checkTable">Ver Tabela</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {

    return {
      form: {
        ddd: "",
        telefone: "",
        phoneType: "",
        nome: "",
        sobrenome: "",
        isActive: ""
      }
    };

  },
  methods: {
    checkTable() {
      this.$router.push("/contatos");
    },

    handleValidation(input){
      let ddd = input.ddd;
      let telefone = input.telephone;
      let erros = [];

      if(ddd.length !== 2){
        erros.push('DDD Invalido!');
      }

      if(telefone.length !== 9){
        erros.push('Telefone Inválido');
      }
      return erros;
    },


    handleRegister(e) {
      e.preventDefault();

      let storage = localStorage.getItem("WaitList");

      console.log("storage linha 85", storage);

      let storageList = {
        id: Math.floor(Math.random() * 100),
        ddd: this.form.ddd,
        name: this.form.nome,
        lastName: this.form.sobrenome,
        telephone: this.form.telefone,
        phoneType: this.form.phoneType,
        isActive: this.form.isActive
      };

      //validation
      const erros = this.handleValidation(storageList);

      if(erros.length){
        alert(erros.join('\n'));
      } else {
        if (storage) {
          storage = JSON.parse(storage);
          storage.push(storageList);
        } else {
          storage = [storageList];
        }

        localStorage.setItem("WaitList", JSON.stringify(storage));
        this.checkTable();
      }
    }
  }
};
</script>

<style lang="scss" scope>
@import "../assets/scss/generic/colors";

.form-sign {
  > .title {
    text-align: center;
    text-transform: uppercase;
    font-size: 23px;

    @media only screen and (min-width: 764px) {
      margin-top: 10px;
    }
  }

  .form {
    display: grid;
    font-size: 20px;
    padding: 0 10px;
    row-gap: 20px;

    > .sub-group {
      &::-webkit-outer-spin-button,
      input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
      }
      > .ddd {
        display: none;
        margin: 0;
      }

      > .sub-input-group {
        display: flex;
        flex-direction: column;

        > .input {
          height: 66px;
          margin-top: 10px;
        }
      }
    }

    @media only screen and (min-width: 764px) {
      display: grid;
      grid-template-rows: repeat(4, 1fr);
      grid-template-columns: repeat(4, 1fr);
      grid-column-gap: 20px;
      margin-bottom: 20px;

      > .sub-group {
        display: grid;
        grid-template-columns: 50px 200px;
        grid-column-gap: 40px;

        > .ddd {
          display: inherit;
          > .input {
            height: 66px;
            width: 60px;
            margin-top: 10px;
          }
        }
      }
    }

    > .input-group {
      display: flex;
      flex-direction: column;

      > .input {
        height: 66px;
        margin-top: 10px;
      }

      input[type="radio"]:after {
        width: 15px;
        height: 15px;
        border-radius: 15px;
        top: -2px;
        left: -1px;
        position: relative;
        background-color: $secondary;
        content: "";
        display: inline-block;
        border: 2px solid $primary;
        cursor: pointer;
      }

      input[type="radio"]:checked:after {
        width: 15px;
        height: 15px;
        border-radius: 15px;
        top: -2px;
        left: -1px;
        cursor: pointer;
        background-color: $primary;
        content: "";
        display: inline-block;
        visibility: visible;
        border: 2px solid black;
      }

      @media only screen and(min-width: 764px) {
        &:nth-child(1) {
          grid-row: 1;
          grid-column: 1/2;
        }
        &:nth-child(2) {
          grid-row: 1;
          grid-column: 2/3;
        }
        &:nth-child(3) {
          grid-column: 3/5;
          display: flex;
          margin-top: 20px;
        }
        &:nth-child(4) {
          grid-row: 2;
          grid-column: 1/3;
        }
        &:nth-child(5) {
          grid-row: 2;
          grid-column: 3/5;
        }
      }
    }

    > .radio {
      flex-direction: row;
        > .item {
          margin: 0 15px;
        }

      @media only screen and (min-width: 764px) {
        display: flex;
        align-items: center;

      }
    }
    > .btn {
      height: 72px;
      border-radius: 9px;
      text-transform: uppercase;
      color: white;
      font-weight: 600;
      cursor: pointer;

      &-add {
        background: $primary;
        cursor: pointer;
        @media only screen and (min-width: 764px) {
          grid-column: 4;
          grid-row: 3;
        }

        &:hover {
          opacity: 0.9;
        }
      }
    }

    > .table {
      background: $darkGrey;
      &:hover {
        opacity: 0.9;
      }
      @media only screen and (min-width: 764px) {
        grid-column: 2/4;
        grid-row: 4;
      }
    }
  }
}
</style>
