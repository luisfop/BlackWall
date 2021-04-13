<template>
<div class="scrollable-table">
  <table class="table">
    <tr class="table-head">
      <th>Nome</th>
      <th>Sobrenome</th>
      <th>Telefone</th>
      <th>Tipo de Telefone</th>
      <th>Status</th>
      <th>Action</th>
    </tr>
    <tr class="table-row" v-for="person in waitList" :key="person.id">
      <td>{{person.name}}</td>
      <td>{{person.lastName}}</td>
      <td>{{`(${person.ddd}) ${person.telephone}`}}</td>
      <td>{{person.phoneType}}</td>
      <td>{{person.isActive}}</td>
      <td class="delete">
        <img
          src="../assets/images/Icon ionic-ios-close.svg"
          class="delete-image"
          @click="deleteHandler(person.id)"
        >
      </td>
    </tr>
  </table>
</div>
</template>

<script>
export default {
  name: "List",
  methods: {
    deleteHandler(id) {
      const dataList = JSON.parse(localStorage.getItem("WaitList"));
      const filteredList = dataList.filter(person => {
        return id !== person.id;
      });
      localStorage.setItem("WaitList", JSON.stringify(filteredList));
      this.waitList = filteredList;
    }
  },

  data() {
    return {
      waitList: []
    };
  },
  created() {
    const data = JSON.parse(localStorage.getItem("WaitList"));
    this.waitList = data;
  },

};
</script>

<style lang="scss" scoped>

.scrollable-table {
  overflow-x: auto;
 flex-grow: 1;

  > .table {
    font-family: Arial, Helvetica, sans-serif;
    border-collapse: collapse;   
    border: solid black;
    border: 1px solid #ddd;
    padding: 8px;
    width: 80vw;
    margin-left: auto;
    margin-right: auto;


    > .table-head {
      background-color: #131c20;
      color: white;
      padding-top: 12px;
      height: 50px;
    }
    > .table-row {
      &:nth-child(even) {
        background-color: #f9f8f8;
      }
      height: 47px;
      text-align: center;

      > .delete {
        cursor: pointer;
      }
    }
  }
}
  

</style>
